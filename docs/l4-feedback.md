# L4 pack: sub-minute feedback

**Not applied.** The L3 pre-commit budget (under 30s) stays as it is. This pack adds a one-minute cap on the CI fast path.

## Opt in

1. Confirm `{{STACK_TEST_FAST}}` can finish in under 60 seconds.
2. Copy `timeout-minutes` and the elapsed check from [optional/l4/sub-minute-feedback/unit-job.yml](../optional/l4/sub-minute-feedback/unit-job.yml) onto the `Fast unit` job in `.github/workflows/ci.yml`.
3. Re-score Style and validation in [AUTONOMY.md](AUTONOMY.md). It can move to 4. Overall stays 3 until every pillar is at least 4.

Do not weaken the pre-commit 30s budget to make CI look fast.
