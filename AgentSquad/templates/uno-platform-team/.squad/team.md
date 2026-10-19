# Squad Team

> Cross-platform .NET app with Uno Platform.

## Coordinator

| Name | Role | Notes |
|------|------|-------|
| Squad | Coordinator | Routes work, enforces handoffs and reviewer gates. |

## Members

| Name | Role | Charter | Status |
|------|------|---------|--------|
| Lead | Architecture & coordination | .squad/agents/lead/charter.md | Active |
| Frontend | Frontend C#/XAML Expert | .squad/agents/frontend/charter.md | Active |
| Tester | QA Engineer | .squad/agents/tester/charter.md | Active |
| Reviewer | Code Reviewer | .squad/agents/reviewer/charter.md | Active |
| Docs | Documentation Specialist | .squad/agents/docs/charter.md | Active |
| Scribe | Session Logger | .squad/agents/scribe/charter.md | Active |
| Rai | RAI Reviewer | .squad/agents/rai/charter.md | Active |
| Fact Checker | Verifier | .squad/agents/fact-checker/charter.md | Active |

## Coding Agent

<!-- copilot-auto-assign: false -->

| Name | Role | Charter | Status |
|------|------|---------|--------|
| @copilot | Coding Agent | — | 🤖 Coding Agent |

### Capabilities

**🟢 Good fit — auto-route when enabled:**
- Bug fixes with clear reproduction steps
- Test coverage (adding missing tests, fixing flaky tests)
- Lint/format fixes and code style cleanup
- Dependency updates and version bumps
- Small isolated features with clear specs
- Boilerplate/scaffolding generation
- Documentation fixes and README updates

**🟡 Needs review — route to @copilot but flag for squad member PR review:**
- Medium features with clear specs and acceptance criteria
- Refactoring with existing test coverage
- API endpoint additions following established patterns
- Migration scripts with well-defined schemas

**🔴 Not suitable — route to a squad member instead:**
- Architecture decisions and system design
- Multi-system integration requiring coordination
- Ambiguous requirements needing clarification
- Security-critical changes (auth, encryption, access control)
- Performance-critical paths requiring benchmarking
- Changes requiring cross-team discussion

## Project Context

- **Owner:** {{owner_name}}
- **Project:** {{project_description}}
- **Stack:** .NET, C#, XAML, Uno Platform
- **Created:** {{created_at_iso8601}}
