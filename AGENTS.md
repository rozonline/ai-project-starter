# AGENTS.md

Instructions for coding agents on `{{PROJECT_NAME}}`. Humans: start at [README.md](README.md). Scoring: [docs/AUTONOMY.md](docs/AUTONOMY.md).

## Identity

- Project: `{{PROJECT_NAME}}`
- Owner: `{{OWNER}}`, GitHub `@rozonline` only
- Audience: personal projects only
- Stack: `{{STACK}}` (unset). Do not add a framework, app source, or lockfile until the owner sets the stack
- License: MIT (already in `LICENSE`)

`CLAUDE.md` only points here. Edit this file, not a second copy of the rules.

## Setup

```bash
git config core.hooksPath .githooks
cp .env.example .env
# {{STACK_SETUP}}
```

## Build

```bash
# {{STACK_BUILD}}
```

There is no build until `{{STACK}}` is set. The lockfile is added with the stack, not before.

## Test

```bash
# Fast unit: {{STACK_TEST_FAST}}
# Full suite: {{STACK_TEST_FULL}}
```

CI runs those as separate jobs. Rules: [docs/TESTING.md](docs/TESTING.md).

## Run

```bash
# {{STACK_RUN}}
```

## Deploy

None. No deploy scripts, no export scripts, no production wiring. Do not add them unless the owner asks in a later change.

## Danger list

Do not:

- Add an owner other than `@rozonline` (never `vueintl`, never `@mike-roz`)
- Commit secrets, `.env`, or credentials
- Add a stack, framework, application source, or lockfile while `{{STACK}}` is unset
- Let `.githooks/pre-commit` exceed 30 seconds
- Turn on a coverage percent gate (that is an L4 pack, off by default)
- Add production deploy or export scripts
- Log secrets, or log an error without a correlation or trace id ([docs/LOGGING.md](docs/LOGGING.md))
- Treat files under `optional/l4/` or `docs/l4-*.md` as active rules

## Conventions

- Small diffs. One concern per change.
- Short files. Split a file that no longer fits on one screen.
- Boundary: this repo is the L3 floor. Application code, if the owner adds it later, stays out of hook stubs, score docs, and L4 packs.
- Agent-facing rules live in this file.
- Leave `{{TOKEN}}` placeholders intact unless you are the kickoff skill filling them.
- `CODEOWNERS` stays `* @rozonline`.

## Hooks

Enable in each clone:

```bash
git config core.hooksPath .githooks
```

`.githooks/pre-commit` runs format (`{{STACK_FORMAT}}`) and lint (`{{STACK_LINT}}`). Both are empty until the stack is chosen. The hook must exit in under 30 seconds.

## Observability

Follow [docs/LOGGING.md](docs/LOGGING.md). Wiring the logger (`{{STACK_LOGGER}}`) waits for the stack. The checklist itself is required now.

## Security

Follow [docs/SECURITY.md](docs/SECURITY.md).

## Level 4

Off. Packs: [optional/l4/README.md](optional/l4/README.md). Do not copy them into CI, this file, or the app unless the owner opts in.
