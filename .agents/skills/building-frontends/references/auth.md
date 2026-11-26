# Auth and route guards

Auth is per-project. Confirm the project's scheme before wiring anything; never carry one project's mechanism into another.

Default for a new project:
- Short-lived access token plus a long-lived refresh token that only mints access tokens.
- The access token travels as an httpOnly cookie (preferred for browsers) or a bearer header.
- Never localStorage for tokens. It is a last resort; flag it to the user first.
- On 401, one shared refresh, then retry. The refresh and its failure path: `references/api-client.md`.

Per-user store resets and the sign-in check after an `await`: `SKILL.md`, Data and state. The auth store triggers the resets.

Route guard order:
1. Public routes pass.
2. Hydrate auth (cookie, else refresh).
3. Signed-in users on login or signup redirect to the dashboard.
4. Signed-out users redirect to login.
5. Role check for staff or admin areas.

Cookie sessions need `SameSite` plus a CSRF token or an `Origin` check on state-changing requests (see `securing-applications`).

Guards guard routes only; they do not refetch domain data on every navigation. The role check only hides UI (`references/quality.md`, Security). Nuxt middleware example: `references/nuxt.md`.
