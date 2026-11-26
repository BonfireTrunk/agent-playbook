# Errors, validation, auth flow, response shapes

## Validation: two layers

| Concern | Layer |
|---------|-------|
| Type, shape, required fields, format, length, enums | Schema at the edge |
| Existence and uniqueness | Service |
| State validity (already cancelled, not active) | Service |
| Cross-field rules (end after start) | Service |
| Authorization context (another user's resource) | Service |
| External checks | Service |

- Schema failures reach the handler as validation errors and map to one client-error status (400 by default) so the API has one.
- Check uniqueness in the service for a friendly answer; unique-index rules are in `writing-database-code`.

## Errors

- Services throw typed errors: a status class (bad request, unauthorized, forbidden, not found, conflict, too many requests), a generic message and a stable `errorCode` (`THING_CONFLICT`, `AUTH_REQUIRED`). Optional `data` carries structured fields such as per-field codes.
- Errors that leave the server are generic and driven by `errorCode` (`securing-applications`). The `error` text is a fixed phrase, and no error reveals whether an account or record exists. Internals (SQL text, stack, constraint names, provider payloads) go to the log only.
- One global handler maps everything:

| Source | Status |
|--------|--------|
| Validation or parse failure | 400 |
| Route not found | 404 |
| Typed error | its own status |
| Database unique violation, foreign-key violation | 409 |
| Database NOT NULL violation | 500 (a server bug, not client input) |
| Anything else | 500, generic body |

- Never forward a driver message or constraint name. Keep `data` free of internals and of anything the caller sent.

## Auth flow

- Identity comes from one global step that sets the user, or nothing.
- Guard order: 401 when there is no identity, 403 when the identity lacks the permission. Permission model: `references/permissions.md`.
- Per-request context (request id) is set in one place. Use the client IP only for security log lines, never as a rate-limit key (`securing-applications`).

## Response shapes

| Pattern | Shape |
|---------|-------|
| Single resource | `{ entity: data }` |
| List | `{ entities: [...], total, page, limit }` |
| Creation | status 201, `{ entity: data }` |
| Simple action | `{ success: true, message: "..." }` |
| Error | `{ error, errorCode?, requestId, ts, ...data? }` |

Every error body has the same shape.
