# Work Routing

How to decide who handles what.

## Routing Table

| Work Type | Route To | Examples |
|-----------|----------|----------|
| Architecture and cross-cutting decisions | Lead | App structure, navigation strategy, platform concerns |
| Uno Platform UI and C#/XAML | Frontend | Views, controls, styles, bindings, navigation |
| Project documentation and Uno documentation research | Docs | README and setup updates, developer guides, troubleshooting, release notes |
| Testing and UI verification | Tester | Unit tests, UI tests, Uno Platform App MCP verification |
| Code review | Reviewer | Diffs, regression risks, maintainability, reviewer verdicts |
| RAI and safety review | Rai | Content safety, privacy, fairness, credential checks |
| Verification and challenge | Fact Checker | Fact checks, package/API existence, design assumptions |

Add routes only for agents that exist in this project's casting registry.

## Issue Routing

| Label | Action | Who |
|-------|--------|-----|
| `squad` | Triage: analyze issue, assign `squad:{member}` label | Lead |
| `squad:docs` | Pick up documentation and documentation-research issues | Docs |
| `squad:{name}` | Pick up issue and complete the work | Named member |

### How Issue Assignment Works

1. When a GitHub issue gets the `squad` label, the **Lead** triages it,
   assigns the right `squad:{member}` label, and comments with triage notes.
2. When a `squad:{member}` label is applied, that member picks up the issue
   in their next session.
3. Members can reassign by removing their label and adding another member's.
4. The `squad` label is the inbox for untriaged issues waiting for Lead review.

## Rules

1. **Eager by default** — start useful work in parallel, including anticipatory
   downstream work.
2. **Scribe always runs** after substantial work, in background mode; never
   block the conversation.
3. **Quick facts → coordinator answers directly.** Do not spawn an agent for
   a simple fact.
4. When multiple agents could handle a task, choose the one whose domain is
   the primary concern.
5. **"Team, ..." → fan-out.** Spawn all relevant agents in parallel.
6. Anticipate downstream work; for example, involve Tester early when a
   feature is being built.
7. Issue-labeled work routes to the named member; Lead handles base `squad`
   triage.
