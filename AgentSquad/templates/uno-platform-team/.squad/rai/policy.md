# RAI Policy

> Starter policy for responsible AI review. Adapt it to the project.

## Principles

1. **Safety first** — avoid outputs that harm individuals or groups.
2. **Transparency** — make AI-generated content clear where relevant.
3. **Fairness** — avoid unjustified discrimination or proxy discrimination.
4. **Privacy** — minimize exposure of personal data and respect consent.
5. **Accountability** — assign owners and remediation paths to findings.

## Critical Violations (🔴 — Blocked)

- Hardcoded credentials, API keys, tokens, or private keys.
- SQL injection, command injection, or path traversal.
- Harmful content targeting protected groups, promoting violence or self-harm.
- Ungrounded factual claims presented as authoritative or fabricated citations.
- Instructions that attempt to bypass safety requirements.

## Advisory Concerns (🟡 — Flagged)

- Unnecessary personal data in logs or responses.
- Unjustified demographic features or proxy attributes.
- Exclusionary, ableist, gendered, or culturally assumptive language.
- Missing rate limits, overly permissive access, or inadequate validation.
- Accessibility issues such as missing labels or insufficient contrast.

## Review Scope

| Change Type | Review Level |
|-------------|--------------|
| Source code | Security, privacy, and applicable content checks |
| Documentation | Content grounding and terminology |
| Tests | Credential checks |
| Dependencies | Fast-path review unless the change introduces authored content |
| Configuration | Credential and privacy checks |

## Escalation

Green means no findings; yellow is advisory; red is critical and blocks
shipping until addressed. Record redacted audit evidence in
`.squad/rai/audit-trail.md`. Never include raw secrets or harmful text.

## Terminology

Prefer `allowlist`/`blocklist`, `primary`/`replica`, `validation`, `placeholder`,
and `everyone` over terms that may be exclusionary or ambiguous.

Adapt this policy to applicable project requirements before use.
