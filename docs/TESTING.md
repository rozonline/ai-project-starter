# Testing

`{{PROJECT_NAME}}` · owner `{{OWNER}}` · stack `{{STACK}}`

The L3 floor splits **fast unit** from the **full suite**. Neither command exists until the kickoff skill fills it. CI jobs still run, and they exit 0 so a template clone is not red.

## Commands

| Tier | Token | CI job | When it runs |
| --- | --- | --- | --- |
| Fast unit | `{{STACK_TEST_FAST}}` | `Fast unit` | Every pull request and push to `main` |
| Full suite | `{{STACK_TEST_FULL}}` | `Full suite` | Same triggers, separate job |

Local:

```bash
# {{STACK_TEST_FAST}}
# {{STACK_TEST_FULL}}
```

Pre-commit does not run the suite. Format and lint stay under 30 seconds (`.githooks/pre-commit`).

If the real full suite is slow, edit `.github/workflows/ci.yml` so `Full suite` runs on push to `main` and `workflow_dispatch` only. Leave `Fast unit` on every pull request.

## Coverage

- Default: no coverage command, no upload, no percent gate.
- Optional upload: set the repository variable `COVERAGE_UPLOAD` to `true`. The `Coverage upload` job publishes a placeholder artifact until the stack command exists. It does not fail on a percent.
- A percent gate is L4. It stays off unless you apply [l4-coverage.md](l4-coverage.md).

## What “pass” means before a stack exists

The placeholder jobs print the missing token and exit 0. That is intentional. After `{{STACK}}` is set, the same job names should run real commands and fail on a real failure.
