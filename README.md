# Agent playbook

Engineering skills and global instructions for AI coding agents (Claude Code, Codex, Cursor and
others that read `SKILL.md` files). They set house rules for backends, frontends, databases,
security, privacy-law compliance, tests, code comments, project records and the steps from a
finished change to a merged one. For developers who want their agents to follow one consistent set of conventions across
projects.

## Quick start

Install with the [`skills`](https://github.com/vercel-labs/skills) CLI:

```bash
bunx skills add BonfireTrunk/agent-playbook -g
```

It asks which skills and which agents to install for. To install one skill without prompts:

```bash
bunx skills add BonfireTrunk/agent-playbook -g -s writing-tests -a claude-code -y
```

To update installed skills later, name them so third-party skills are left alone:

```bash
bunx skills update -g writing-tests building-backends
```

## Skills

| Skill | What it covers |
|---|---|
| `auditing-privacy-compliance` | What a product must let its customers do under the GDPR, UK GDPR, US state laws, CCPA, HIPAA, GLBA, COPPA, India's DPDP Act and the EU AI Act: capability checklist, law comparison, research method, gap-analysis report |
| `building-backends` | Backend rules in any language: layers, one owner per rule, validation, typed errors and error codes, auth, bitmask permissions, response shapes, public API versioning, package layout, jobs, dead code |
| `building-elysia-servers` | JavaScript backends on Bun with Elysia: routes, services, TypeBox, auth guards, logging, config, Redis or Valkey, BullMQ, payments |
| `building-frontends` | Vue, Nuxt, React and Next.js on Bun with Vite and Tailwind CSS v4: components, state, API client, auth, forms, accessibility, naming |
| `delegating-to-codex` | Handing implementation or review work to the OpenAI Codex CLI, only when the user asks for it |
| `maintaining-project-records` | Project memory in the repo: handoff, todo, questions, requirements documents with a feature index, README, parallel agent sessions |
| `preparing-changes-for-merge` | From finished change to merge: checking the branch against the skills, fresh-context review, answering findings, commit and PR text |
| `securing-applications` | Password hashing, injection, authorization, CSRF, CORS, XSS, secrets, security logging, rate limits, uploads, error responses |
| `writing-code-comments` | Whether a comment is needed, where it goes and how to word it |
| `writing-database-code` | PostgreSQL and Drizzle: schema, status columns, unique indexes, idempotent writes, transactions, migrations, mappers |
| `writing-go-code` | Go: errors, context, concurrency, slog, testing, layout, cobra, net/http, pgx and sqlc, GoReleaser |
| `writing-java-code` | Java backends: JDK features, Gradle with Kotlin DSL, multi-module layout, jOOQ, Jackson, logging, JUnit and Testcontainers |
| `writing-tests` | Test scope and levels, fixtures, fakes, injected clocks, timeouts, concurrency tests, guard scripts, reading results |

Each skill is a folder under `.agents/skills/` with a `SKILL.md` that the agent loads first and a
`references/` folder it opens only for the step at hand.

## Global instructions

`.agents/AGENTS.md` holds the defaults that apply to every project: working style, how to ask
and report, safety, git, dependencies and helper agents. `.agents/instructions/` holds the parts
read on demand (environment, git, product). Skills link to them by their installed path under
`~/.agents/`, so link them there from a clone:

```bash
git clone https://github.com/BonfireTrunk/agent-playbook.git
mkdir -p ~/.agents
ln -s "$PWD/agent-playbook/.agents/AGENTS.md" ~/.agents/AGENTS.md
ln -s "$PWD/agent-playbook/.agents/instructions" ~/.agents/instructions
```

Then point your agent at `~/.agents/AGENTS.md`. For Claude Code, add this line to
`~/.claude/CLAUDE.md`:

```text
@~/.agents/AGENTS.md
```

## Layout

```text
.agents/
  AGENTS.md          global defaults for every project
  instructions/      environment, git and product rules, read on demand
  skills/<name>/     SKILL.md plus references/
  todo.md            open work on this repo
```

## Contributing

Work on a branch off `main` and squash-merge it. Before a PR, check that every skill still loads:

```bash
bunx skills add . --list
git diff --check main...HEAD
```

Each rule has one owner: a rule that two skills need lives in one of them, and the other links to
it. The `preparing-changes-for-merge` skill describes the review and the commit and PR text.

## Licence

[Mozilla Public License 2.0](LICENSE).
