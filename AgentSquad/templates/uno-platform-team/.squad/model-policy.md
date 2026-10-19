# Model Policy

> Team-specific model guidance that extends Squad's built-in model selection
> (`.squad/templates/model-selection-reference.md`). Charters name one
> `Preferred` model; this file covers provider choice, fallback chains, and
> cross-family review.

## Provider Profiles

Each agent charter lists OpenAI, Anthropic, and Google options per task. To
standardize on one provider, copy a profile from the template's
`model-profiles/` folder into `.squad/config.json`. `agentModelOverrides` is
Squad's Layer 0 and takes precedence over charter preferences.

| Profile | Use when |
|---------|----------|
| `balanced.json` | Default. GPT for code, Gemini for RAI, cross-family review. |
| `anthropic.json` | Claude for authoring and review; Gemini for RAI and fact checks. |
| `openai.json` | GPT for authoring; Claude reviews and Gemini runs RAI. |

Both provider profiles keep RAI and fact checks on another model family.
If org policy blocks a provider entirely, replace those entries too.
| `economy.json` | Cost matters most; keeps code-writing agents on standard tier. |

When the user says "use Claude" (or another provider) for the session, stay
within that provider through the fallback chain before omitting the model
parameter.

## Fallback Chains

Retry silently with the next model when a spawn fails because a model is
unavailable (plan, org policy, rate limit, or deprecation). Never fall back
up a tier.

```
Premium:  gpt-5.6-sol → claude-opus-5.5 → claude-opus-5 → gemini-3.1-pro → (omit model param)
Standard: gpt-5.6-terra → claude-sonnet-5.5 → claude-sonnet-5 → gemini-3.1-pro → (omit model param)
Fast:     gpt-5.6-luna → claude-haiku-4.5 → gpt-5.4-mini → gpt-5-mini → (omit model param)
```

Provider-pinned chains:

```
Anthropic: premium claude-opus-5.5 → claude-opus-5 → claude-opus-4.8
           standard claude-sonnet-5.5 → claude-sonnet-5 → claude-sonnet-4.6
           fast claude-haiku-5.5 → claude-haiku-4.5
OpenAI:    premium gpt-5.6-sol → gpt-5.5
           standard gpt-5.6-terra → gpt-5.3-codex → gpt-5.4
           fast gpt-5.6-luna → gpt-5.4-mini → gpt-5-mini
Google:    standard gemini-3.1-pro; fast gemini-3.8-flash
```

## Cross-Family Review

Reviewer, Rai, and Fact Checker should run on a different model family than
the agent that produced the change. Same-family reviewers share the author's
blind spots. If Frontend wrote the change on `gpt-5.6-terra`, review it on
`claude-opus-5.5` or `gemini-3.1-pro`, and the reverse.

## Model Availability

Model IDs use GitHub Copilot's dotted form (`claude-opus-5.5`), not the
Anthropic API form (`claude-opus-5-5`). Availability depends on the Copilot
plan and org policy:

- Squad 0.13.x verifies `claude-opus-5`, `claude-sonnet-5`,
  `claude-haiku-4.5`, the `gpt-5.6-*` family, and `gemini-3.1-pro`.
- `claude-fable-5.1`, `claude-opus-5.5`, `claude-sonnet-5.5`,
  `gemini-3.8-flash`, and `grok-4.7` are newer than Squad's verified
  catalog. Squad passes unknown IDs through and falls back when a model is
  unavailable.
- `claude-haiku-5.5` may not be enabled in Copilot yet. Use
  `claude-haiku-4.5` until it is.
- `claude-fable-5.1` is Anthropic's most capable model and costs more than
  Opus. Reserve it for the hardest architecture decisions and contested
  reviews; never make it a default.

Run `copilot` and use `/model` to see the models your account can use, then
remove unavailable IDs from your project's config.
