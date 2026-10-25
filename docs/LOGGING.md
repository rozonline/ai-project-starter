# Logging

`{{PROJECT_NAME}}` · owner `{{OWNER}}` · stack `{{STACK}}`

L3 observability is this checklist. The app logger (`{{STACK_LOGGER}}`) is wired when the stack exists. Do not add a logging library to this template.

## Checklist

- [ ] Logs are structured JSON, one object per line
- [ ] Each line has `timestamp` (ISO-8601), `level`, and `message`
- [ ] Each line has a correlation or trace id field named `traceId`
- [ ] Every error log includes `traceId` (no error line without it)
- [ ] `traceId` comes from the incoming request header `TRACE_ID_HEADER` (default `x-trace-id` in `.env.example`) or a new id if the header is absent
- [ ] Logs do not contain secrets, tokens, or raw `.env` values
- [ ] Stack wiring is recorded by replacing `{{STACK_LOGGER}}` with the module that emits these lines

## Shape

```json
{"timestamp":"2026-01-01T00:00:00Z","level":"error","message":"request failed","traceId":"4f3c0a"}
```

## Not in L3

Metrics, span trees, and vendor APM are the L4 pack [l4-observability.md](l4-observability.md). Leave them unused until the owner opts in.
