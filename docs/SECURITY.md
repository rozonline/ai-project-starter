# Security and governance

`{{PROJECT_NAME}}` · owner `{{OWNER}}` · GitHub `@rozonline` only.

No deploy scripts and no export scripts ship with this floor.

## Branch protection

After the first green CI run, protect `main`. For a single owner, require checks, not a second reviewer (GitHub will not let you approve your own pull request).

Set a branch ruleset (or classic branch protection) on `main`:

- Block force pushes
- Block deletion
- Require a pull request before merging
- Required approvals: 0
- Require status checks: `CI / Fast unit` and `Dependency review` (use the names GitHub shows after the first run)
- Do not grant bypass or admin rights to any account except `@rozonline`

`CODEOWNERS` is `* @rozonline`. Do not add `vueintl` or `@mike-roz`.

## Secret scanning

In the generated repository: **Settings → Code security → Secret scanning → Enable**, then enable **Push protection**.

`.env` is gitignored. Only `.env.example` is committed. Do not put real credentials in workflows.

The dependency-review workflow prints this reminder on pull requests. It is not a secret scanner.

## Dependency review

Workflow: `.github/workflows/dependency-review.yml`.

- On a **public** repository the official dependency-review action runs. `continue-on-error` stays on until a lockfile exists and you have seen the check pass. Then set `continue-on-error` to `false`.
- On a **private** repository the action is skipped, because GitHub often requires an extra license for that API. The reminder step still runs. Turn the action on when dependency review is available for that repo.
- This template has no lockfile. A review with no manifests is a no-op, not a failure of the floor.

## Out of scope

Production deploy, release signing, and export pipelines are not part of the L3 floor.
