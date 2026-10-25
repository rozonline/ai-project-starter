# L4 pack: coverage percent gate

**Not applied.** L3 allows an optional coverage **upload** (`COVERAGE_UPLOAD=true`) and forbids a percent gate.

## Opt in

1. Choose a number and replace `{{COVERAGE_MIN}}` in [optional/l4/coverage-gate/coverage-job.yml](../optional/l4/coverage-gate/coverage-job.yml).
2. Make `{{STACK_TEST_FULL}}` (or the fast command) write `coverage/percent.txt` as an integer.
3. Copy that job into `.github/workflows/ci.yml`.
4. Re-score Testing. It can move to 4.

If you only want an artifact, use the L3 upload job and do not copy this pack.
