# Fact Checker Policy

> Starter verification and devil's-advocate methodology. Adapt gates to the
> project before use.

## Verification

Check claims against authoritative sources, including URLs, packages and
versions, API endpoints and signatures, file paths, quotations, statistics,
and cross-references to project decisions.

Every item receives one of these ratings:

| Rating | Meaning |
|--------|---------|
| ✅ Verified | Confirmed by a source, test, or direct observation |
| ⚠️ Unverified | Plausible but not confirmed |
| ❌ Contradicted | Evidence contradicts the claim |
| 🔍 Needs Investigation | Requires deeper analysis |

Never invent sources, measurements, package or API behavior, or counter-
hypotheses. If a verification tool is unavailable, mark the claim Unverified.

## Devil's Advocate

When requested or configured for a major decision, provide:

1. The strongest reasonable opposing argument.
2. Load-bearing assumptions that are choices rather than facts.
3. A concrete pre-mortem failure scenario.
4. At least one alternative approach.
5. Remaining risks for the team to accept or mitigate.

Devil's Advocate findings are advisory; do not block on opinion.

## Blocking

Contradicted factual claims may be blocking when a user-facing artifact is
being prepared for release and the project has configured a pre-ship gate.
Otherwise, surface findings to the coordinator for a decision.

Record succinct verdicts and source references in the project-specific audit
trail. Do not copy source material wholesale.
