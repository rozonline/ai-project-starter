# Autonomy

`{{PROJECT_NAME}}` · owner `{{OWNER}}` · target **Level 3**

Eight pillars. The floor is the Level 3 bar. Level 4 is a pack you opt into. This page is the checklist, not a platform.

Inspiration: Factory-style autonomy maturity. The wording here belongs to this template.

## How to score

1. Score each pillar at the highest level whose bar is fully met (1 through 5).
2. A placeholder counts toward Level 3 when the bar is a file, hook, workflow, or checklist that does not need application code.
3. After a stack is chosen, Build, Testing, and Observability stay at 3 only if the real commands, lockfile, and logger meet the same bar.
4. Overall level is the **minimum** pillar score.
5. Target overall level is 3. Applying an L4 pack can raise that pillar. It does not raise overall until every pillar is at least 4.

## Template scorecard (no application code)

| Pillar | Score | Evidence |
| --- | --- | --- |
| Style and validation | 3 | `.githooks/pre-commit`, 30s budget, enable command documented |
| Build | 3 | Build, test, and run commands in README. Lockfile absent until `{{STACK}}` |
| Testing | 3 | `docs/TESTING.md`, fast unit and full suite jobs, no percent gate |
| Documentation | 3 | `AGENTS.md`, `CLAUDE.md`, danger list, this page |
| Dev environment | 3 | `compose.yaml`, `.devcontainer`. No Node pin |
| Code quality | 3 | Conventions in `AGENTS.md`. `CODEOWNERS` is `@rozonline` |
| Observability | 3 | `docs/LOGGING.md` checklist. Logger wiring waits for `{{STACK}}` |
| Security and governance | 3 | This repo's security notes, secret-scanning reminder, dependency-review stub |
| **Overall** | **3** | Minimum of the pillar scores |

## Pillars

### 1. Style and validation

| Level | Bar |
| --- | --- |
| 1 | No formatter or linter |
| 2 | Format and lint are documented and run by hand |
| 3 | `.githooks/pre-commit` runs format and lint (stubs until `{{STACK}}`) and finishes in under 30s. Enable with `git config core.hooksPath .githooks` |
| 4 | The CI fast path also finishes in under one minute ([l4-feedback.md](l4-feedback.md)) |
| 5 | An agent keeps format and lint green without being asked |

### 2. Build

| Level | Bar |
| --- | --- |
| 1 | Build steps live in someone's head |
| 2 | A build command exists somewhere in the repo |
| 3 | README has discoverable build, test, and run commands. The lockfile is committed when the stack is chosen, and not before |
| 4 | Builds are reproducible and cached |
| 5 | An agent repairs a broken build inside the chosen stack |

### 3. Testing

| Level | Bar |
| --- | --- |
| 1 | No tests |
| 2 | Tests exist and are run by hand |
| 3 | CI has a fast unit job and a separate full suite job. Coverage upload is optional. No percent gate |
| 4 | A coverage percent gate is on ([l4-coverage.md](l4-coverage.md)) |
| 5 | An agent adds tests for its own changes until the suite is green |

### 4. Documentation and instructions

| Level | Bar |
| --- | --- |
| 1 | No agent instructions |
| 2 | README only |
| 3 | `AGENTS.md` covers setup, build, test, deploy, a danger list, and conventions. `CLAUDE.md` points at `AGENTS.md`. This page scores the pillars |
| 4 | Written issue-pickup rules for parallel agents ([l4-parallel-agents.md](l4-parallel-agents.md)) |
| 5 | An agent updates these instructions when behavior changes |

### 5. Dev environment

| Level | Bar |
| --- | --- |
| 1 | Setup is machine-specific |
| 2 | Prose setup steps only |
| 3 | `compose.yaml` and `.devcontainer` stubs exist. Runtime pins, including Node, are added only after `{{STACK}}` is chosen |
| 4 | One command brings up dependencies and the app |
| 5 | An agent can recreate the environment from the repo alone |

### 6. Code quality

| Level | Bar |
| --- | --- |
| 1 | No shared rules |
| 2 | Informal habits |
| 3 | Size and boundary conventions are in `AGENTS.md`. `.github/CODEOWNERS` is `@rozonline` only |
| 4 | Boundary or complexity checks run in CI |
| 5 | An agent refactors inside those boundaries |

### 7. Observability

| Level | Bar |
| --- | --- |
| 1 | Print debugging |
| 2 | Unstructured logs |
| 3 | `docs/LOGGING.md`: structured JSON, and a correlation or trace id on every error. App wiring may wait for the stack |
| 4 | Metrics and trace spans, not only error ids ([l4-observability.md](l4-observability.md)) |
| 5 | An agent uses that telemetry to diagnose failures |

### 8. Security and governance

| Level | Bar |
| --- | --- |
| 1 | No checks |
| 2 | Secrets are gitignored |
| 3 | Branch-protection notes, a secret-scanning reminder, and a dependency-review workflow stub. No deploy or export scripts |
| 4 | Required checks and secret push protection are enabled on the live repository |
| 5 | An agent remediates dependency and secret findings inside owner rules |

Level 4 on this pillar is repository settings, not a file pack. The file packs are the other three L4 docs plus coverage.
