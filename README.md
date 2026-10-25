# {{PROJECT_NAME}}

Stack-agnostic **AMM Level 3** floor for a personal AI project.

| | |
| --- | --- |
| Owner | `{{OWNER}}` (GitHub `@rozonline` only) |
| Stack | `{{STACK}}` (unset in this template) |
| License | MIT |
| Maturity | Level 3 floor. Level 4 packs are opt-in |

This repository is a [GitHub template](https://github.com/rozonline/ai-project-starter). Use **Use this template** to start a project. It is usable before any kickoff skill runs. The skill later replaces `{{placeholders}}` and, if you ask, copies an L4 pack into effect.

Personal projects only. Do not add `vueintl`, `@mike-roz`, or any other owner.

## Enable git hooks

Hooks do not run until this clone points Git at `.githooks`:

```bash
git config core.hooksPath .githooks
```

The pre-commit hook is a format and lint stub. It must finish in under 30 seconds. See [AGENTS.md](AGENTS.md).

## Setup

```bash
git config core.hooksPath .githooks
cp .env.example .env
# {{STACK_SETUP}}
```

Dev environment stubs (no runtime pin, no Node version): [compose.yaml](compose.yaml), [.devcontainer/devcontainer.json](.devcontainer/devcontainer.json).

## Build

No lockfile yet. When a stack is chosen, commit that stack's lockfile and replace the command below. Do not add a lockfile before `{{STACK}}` is set.

```bash
# {{STACK_BUILD}}
echo "No build yet. Stack is {{STACK}}."
```

## Test

Fast unit and full suite are separate CI jobs. Coverage upload is off. There is no coverage percent gate.

```bash
# Fast unit: {{STACK_TEST_FAST}}
# Full suite: {{STACK_TEST_FULL}}
echo "No tests yet. See docs/TESTING.md."
```

Details: [docs/TESTING.md](docs/TESTING.md).

## Run

```bash
# {{STACK_RUN}}
echo "No run command yet. Stack is {{STACK}}."
```

## Deploy

No deploy and no export scripts. Do not add production deploy wiring in this template.

## Placeholders

The kickoff skill substitutes these tokens. Until then they stay literal.

| Token | Filled with |
| --- | --- |
| `{{PROJECT_NAME}}` | Repository or product name |
| `{{OWNER}}` | `rozonline` |
| `{{STACK}}` | Chosen stack (not decided here) |
| `{{STACK_SETUP}}` | Dependency install |
| `{{STACK_BUILD}}` | Build command |
| `{{STACK_TEST_FAST}}` | Fast unit command |
| `{{STACK_TEST_FULL}}` | Full suite command |
| `{{STACK_RUN}}` | Local run command |
| `{{STACK_FORMAT}}` | Formatter in `.githooks/pre-commit` |
| `{{STACK_LINT}}` | Linter in `.githooks/pre-commit` |
| `{{STACK_LOGGER}}` | Where the app logger is wired |
| `{{COVERAGE_MIN}}` | L4 coverage gate only. Unset here |

## Docs

- [AGENTS.md](AGENTS.md) agent instructions, conventions, danger list
- [CLAUDE.md](CLAUDE.md) pointer to AGENTS.md
- [docs/AUTONOMY.md](docs/AUTONOMY.md) eight pillars, L1–L5, scoring
- [docs/TESTING.md](docs/TESTING.md) fast unit vs full suite
- [docs/LOGGING.md](docs/LOGGING.md) structured log checklist
- [docs/SECURITY.md](docs/SECURITY.md) branch protection, secret scanning, dependency review

## Level 4 (off)

Packs live in the repo and do nothing until you opt in. See [optional/l4/README.md](optional/l4/README.md).

- [docs/l4-feedback.md](docs/l4-feedback.md) sub-minute CI feedback
- [docs/l4-observability.md](docs/l4-observability.md) metrics and tracing
- [docs/l4-parallel-agents.md](docs/l4-parallel-agents.md) parallel issue pickup
- [docs/l4-coverage.md](docs/l4-coverage.md) coverage percent gate
