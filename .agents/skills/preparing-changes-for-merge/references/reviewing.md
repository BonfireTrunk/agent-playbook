# Reviewing a change

Open when checking a finished branch against the skills before its PR, when reviewing a diff
(your own before a PR, a helper's, or someone else's), when reporting findings, or when answering
them.

## Skills that apply

The author's check before the PR and the reviewer both read the change against the skills that
match what it touches. A rule a skill sets is a finding when the change breaks it.

| The change touches | Check against |
|---|---|
| Backend code: handlers, services, jobs | `building-backends`, plus the language skill (`writing-go-code`, `writing-java-code` or `building-elysia-servers`) |
| Frontend code | `building-frontends` |
| SQL, schema, migrations, queries | `writing-database-code` |
| Sign-in, tokens, permissions, input handling, uploads, secrets | `securing-applications` |
| Tests | `writing-tests` |
| Code comments | `writing-code-comments` |
| Behaviour of a feature | `maintaining-project-records`, Features: its section, the feature index, `Depends on:` lines, the features that rely on it |
| Project records: handoff, todo, questions | `maintaining-project-records` |
| Anything | the repo's own `AGENTS.md` or `CLAUDE.md` |

Organisation and duplication get the closest look, because they show only across the whole
branch. Their rules are owned by the skills below; apply those sections rather than a summary of
them here:

| Check | Backend | Frontend |
|---|---|---|
| Organisation | `building-backends`: Layers, Package layout, Where shared code goes. The language skill's layout rules. | `building-frontends`: When to split, Structure and imports |
| Duplication | `building-backends`: One owner per rule, Finding duplication | `building-frontends`: Reuse |

For other code, the repo's own conventions decide both.

## Before the PR

Once the branch is complete, go through the whole branch diff once (`git diff <base>...HEAD`)
against the skills that match it, with the organisation and duplication sections first. Fix what
it finds, then hand the branch to the reviewer.

## Who reviews

- A reviewer with a fresh context: a helper agent or a separate session that did not write the
  change. The session that wrote it has already accepted its own reasoning. Where the agent has a
  built-in review command that runs in a helper, that counts.
- Give the reviewer the diff, what the change is meant to do, and the skills from the table above
  that match the change, by name, including their organisation and duplication sections. A
  helper with a fresh context knows none
  of them unless its brief says so. Do not give it your conclusion: a reviewer handed "this is
  correct" tends to agree.

## What the reviewer checks

- Does the change do what it says it does?
- Does it fit the code around it, the repo's conventions and the skills that match it, including
  their organisation and duplication rules?
- Does it break something else: a caller, a second writer of the same data, an error path?
- For a bug fix: does it fix the cause, or only the case that was reported?
- Read the test diff first. A loosened, deleted or newly skipped assertion is a finding unless
  the behaviour it pinned was meant to change.
- Does the diff change anything outside the task? An unrequested edit is a finding.

Correctness comes first. What a formatter, a linter or a type checker already enforces is not a
finding. Plain JavaScript has no type checker, so there type misuse is a finding: a wrong argument
shape, a value that may be `undefined` used as if set, a string where a number is expected.
TypeScript code has one; leave that to it.

## Reporting findings

- **Evidence.** Every finding cites a file and line and says which input or state leads to which
  wrong result. Read the code path before claiming it; a guess from a name is not a finding.
- **Labels.** Each finding carries one:

  | Label | Meaning |
  |---|---|
  | Important | Breaks behaviour, loses or leaks data, or blocks undoing the change. Fix before merge. |
  | Nit | Minor. At most five per review. |
  | Pre-existing | A real problem the change did not introduce. Listed apart, so it does not read as the author's mistake. |

- **The class, not the line.** When the same mistake appears in several places, report it once as
  a class and list the places, so the author fixes every one.
- **The summary starts with a count** per label, most severe first. When nothing needs fixing,
  say so in plain words.

## Answering findings

- Every finding gets an answer: fixed, with where; or closed with a reason. The reasons are
  "wrong" with the evidence, "intentional" with why, or "not in this change" with where it is
  recorded instead.
- Fix the whole class a finding names, not only the line it cites.
- A pre-existing problem does not widen the change. Record it where the project keeps open work
  and tell the user.

## Rounds

- After fixes, the next round reviews only the new diff, not the whole change again.
- Never repeat a finding that was already reported or closed with a reason. A reviewer that
  disagrees with a closure says so once, with evidence, and leaves the decision to the user.
- Three rounds at most. If the third still finds Important problems, stop fixing line by line:
  step back, rethink the approach and tell the user. A reviewer and an author that are both
  agents can otherwise keep each other busy without the change getting better.
