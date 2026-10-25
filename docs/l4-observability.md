# L4 pack: observability

**Not applied.** L3 remains the [LOGGING.md](LOGGING.md) checklist (JSON lines, `traceId` on errors).

## Opt in

1. Read [optional/l4/observability/signals.md](../optional/l4/observability/signals.md).
2. When `{{STACK_LOGGER}}` exists, extend it with those fields. Do not add a vendor SDK to the template floor.
3. Re-score Observability. It can move to 4.

Leave this pack unused if the app only needs error correlation ids.
