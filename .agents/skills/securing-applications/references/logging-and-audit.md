# Logging and audit

## Where an event goes

| Event | Destination |
|---|---|
| Action by a known user that affects that user | audit row |
| Failed sign-in for a known user | audit row, plus security log line |
| Sign-in attempt for an unknown identifier | security log line only |
| Refusal of a deactivated account | security log line only, same response as any other refusal |

The deactivated-account row is log-only by default: the refusal must look identical to any other, and an audit row would add an observable difference if the audit is user-visible.

## Security log line

- Never: raw identifier, password, token, cookie value, authorization code, other personal data.
- Hash with a keyed function (HMAC) over the normalised identifier (trimmed, case-folded), so the same input always gives the same value and a leaked log cannot be reversed by guessing.
- Route every line through one helper. A call site cannot add a field the helper does not take.

## Audit row

- Actor, action, target, time, and a result.
