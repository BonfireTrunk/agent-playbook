---
name: writing-tests
description: "Sets test discipline: scope, the unit, integration and end-to-end levels and when each runs, fixtures, hand-written fakes, injected clocks, timeouts, concurrency tests, structural guard scripts, and reading results after a targeted run. Has stack notes for the JVM, PostgreSQL lock waits and workflow test servers with time skipping. Use when writing, changing, reviewing or debugging tests in any language, or when the task mentions mock, mocking, coverage, snapshot, Temporal, fixtures, flaky CI, a hanging or slow test, a race, or '0 tests ran'."
---

# Test discipline

## Scope

- Write unit tests on functions and methods by default. They run with no live infrastructure: no database, cache, queue or network.
- For integration, component or end-to-end tests, check the project's conventions first. If they do not say, ask the user which levels to write before writing any.
- Sensible tests only: workflows, edge cases, positive and negative paths. No padding.
- Every test pins a behaviour that can regress: a transformation, a branch, a boundary, a contract with consequences. No field-passthrough checks, "does not crash" checks, defaults the language already guarantees, or the same logic through trivially different inputs. A table test is fine only when each row pins a distinct behaviour. Test count is not a quality signal. When a helper agent writes tests, state this rule in its brief and prune violations.
- A test that asserts a constant equals the same literal written in the test is padding. Instead, move the decision (for example, mapping an error code to a message and a next step) into a pure helper and test the helper.
- When a test needs a constant that is not accessible from the test (for example a limit declared private to its package or module), widen its visibility so the test can import it. Do not copy its number into the test; the test then follows the source.
- During a large structural refactor, if the user agrees, defer test writing: check with compile-only runs, then do a planned test pass on its own branch.

## Levels and when they run

| Level | What it touches | When it runs |
|---|---|---|
| Unit | Code in one process only: no database, cache, queue, network, container or browser | After each significant chunk of work, and before every merge |
| Integration | Real infrastructure: a database, cache, queue, container or another process | With the unit tests, before a PR merges |
| End-to-end | The whole app through its UI or public API | Only when the user asks |

- A test that needs a database is an integration test, whatever folder it sits in.
- Each level has its own command (a folder, a tag or a test task), so a unit run never starts infrastructure and stays fast enough to run often.
- A slow unit test is a finding: put the slow part (I/O, sleeps, the wall clock) behind a fake, or move the test to the integration level.
- Static checks (formatter, linter, type checker) are faster than any test level: run them after each edit.
- A browser check of the UI is end-to-end work and runs only when asked, with one exception: after fixing a reported UI bug, verify that bug's flow alone in the browser. Run it on a helper in the background, so no other work waits on it.
- A failing assertion is fixed at its cause. Never loosen, delete or skip it to get a green run; change it only when the behaviour it pins is meant to change.

## Fakes and fixtures

- Write fakes by hand. Do not use a mocking library. When a port gains a method, update its fakes in the same change.
- Shape tests pin the exact body (key order and nulls) of key routes. When a response gains a key, update its shape test in the same change.
- Drive the real production path through one shared fixture. A test-local copy of the path drifts silently (a private "submit" helper can drop production steps).
- A test that calls an internal seam directly does not pin the production wiring: revert the call site and it still passes. Drive the real path with a fake transport that fails deterministically.
- Mutation-check a test only when reading it cannot show that it catches the break: a race, a guard that a second guard may also cover, wiring through several layers. Break the code on purpose, watch the test fail, then restore the code and confirm the diff is clean. A simple check whose failing case is plain from the code needs no mutation run.
- A test that deliberately creates data that breaks a database-wide invariant check (for example a row with no parent) deletes that data when it finishes, so later checks do not fail.
- Test classes that share one database each use their own range of ids (for example 1000-1999 for one class, 2000-2999 for the next) so they cannot collide.

## Output, time and assertions

- When a type on one side of a boundary mirrors an enum or constant on the other (a wire type and its domain enum, a client constant copied from the server), add a test that pins the two equal.
- Test output is pristine: a warning in the output is a finding. A test that triggers a log line on purpose captures and asserts it. Never lower the root log level to hide it.
- Time comes from an injected clock, never the wall clock. Assert on recorded events (for example, that a timer-started event appears in the workflow history) rather than elapsed time, which drifts under time-skipping servers.
- Two timers with the same budget race: when a library's request timeout and your own deadline are equal, either error can surface. Make the test assert one fixed message for every timeout path, and give the two timers different budgets.
- To check that an error does not echo input, assert on the specific response field, not the whole body. Random ids in the body can contain the probe.
- A rename of how a log line names something can change how many lines a throttle lets through. Say so in the change and update the tests that count lines.

## Timeouts, hangs and flakes

- Every test module sets a default per-test timeout, so one hung test cannot hold a shared lock for everyone. Know what the timeout can stop: see the stack notes below.
- A fix for a hang or flake always gets the mutation check above: reading the test cannot show it catches the break.
- For racing requests, helper waits and child processes, read `references/concurrency-tests.md`.

## Running tests

- A run is red or green only on its own evidence: the command's own exit code and the result files it wrote. Without both it did not finish: say so and run it once more. The usual ways the evidence gets lost:
  - After a targeted run, check that the result files list the classes you meant. A test-name filter that matches nothing passes silently.
  - Never pipe a gate's exit code away. Redirect output to a file and print `EXIT=$?` explicitly. Gate on the command's own exit code. A pipe reports its last command, also inside `bash -c '...'` and inside an `&&` chain: `build | tail -5; echo EXIT=$?` prints `EXIT=0` for a failed build.
  - An exit code above 128 with no result files means the run was killed from outside (143 is SIGTERM, 137 is SIGKILL). That is not a test failure.
- A change to a shared fixture (base class, seed helper, race helper) means the whole module's tests, not only the edited classes: every caller depends on it.
- When one change turns many tests red at once (a newly required header, a stricter parser), find the shared cause before fixing tests one by one: run the whole module once for the full red list, then fix the shared test client or helper first.
- Test runs that share a machine follow the project's lock rule.
- The build fails on any test that prints to stdout or stderr, and on any skipped test outside a small allowlist: an assumption-skip on a missing tool otherwise reads green.

For layering or cycle guard scripts and their tests, read `references/structural-guards.md`.

## Stack notes (open only for that stack)

| Open | When |
|---|---|
| `references/jvm.md` | JVM test timeouts, interrupts, shared containers |
| `references/postgresql.md` | tests that wait on database locks |
| `references/temporal-test-server.md` | workflow tests on a time-skipping test server |
