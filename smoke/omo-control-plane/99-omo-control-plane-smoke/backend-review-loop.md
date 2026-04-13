# Backend Review Loop

- work item: `99-omo-control-plane-smoke`

## Tokens

- [ ] backend-request-1
- [ ] backend-request-2

## Contract

- Stage 3 attempt 1 must return `request_changes` with `SMOKE_BACKEND_FIX_TOKEN: backend-request-1`.
- Stage 3 attempt 2 must return `request_changes` with `SMOKE_BACKEND_FIX_TOKEN: backend-request-2` after token 1 is applied.
- Stage 2 retries must only mark a token as applied when the exact token appears in Prior Review Feedback.
- Stage 3 attempt 3 may approve only after both tokens are marked as applied.

## Applied Notes

- initial: seeded for live provider smoke
