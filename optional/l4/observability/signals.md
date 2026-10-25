# Signals (L4 fragment)

Not wired. Apply only after `{{STACK_LOGGER}}` exists. See `docs/l4-observability.md`.

Keep the L3 error line: JSON, `timestamp`, `level`, `message`, `traceId`.

Add, on request logs as well as errors:

- `spanId` for the current span
- W3C `traceparent` accepted from the inbound request when the caller sends one. `traceId` must match that parent
- Counts the app can emit without a vendor: `requests`, `errors`, `latency_ms`

Do not add a hosted APM SDK, collector, or dashboard to the template.
