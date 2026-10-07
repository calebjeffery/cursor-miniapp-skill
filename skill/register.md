# MiniApp register

Durable memory; later miniApps **RAG** this store.

## Root

```
~/.agents/miniapp-register/
├── INDEX.md
├── projects/<slug>/
│   ├── SETTINGS.md
│   ├── CONTEXT.md
│   ├── STATUS.md
│   ├── research/
│   ├── similar/
│   └── links.md
└── stacks/<stack-slug>/INDEX.md
```

Resolve `~` via `$HOME` / `%USERPROFILE%`.

## Slug

Lowercase kebab-case from project name. On collision, append `YYYY-MM`.

## Write rules

1. **Single source of truth** — decision in `SETTINGS.md` or one ADR; index gists + links.
2. Update `INDEX.md` when adding research or finishing a phase.
3. Update `STATUS.md` after every phase (timestamp + checkbox).
4. **No secrets** — remotes/paths/stack names only.
5. **Cite** — every research claim → primary URL or package page.

## STATUS.md

````markdown
# Status — <slug>

Updated: <ISO-8601>

```
MiniApp progress:
- [ ] 0. Project-creation workflow clarified
- [ ] 1. Register entry created; slug known
- [ ] 2. Settings grill done
- [ ] 3. Stack research worker done; indexed for RAG
- [ ] 4. Similar free projects; continue | review-fork
- [ ] 5. Scaffold + handoff
- [ ] H. Pickup alignment
```

## Notes
- Phase: <n or H>
- Similar-project choice: <continue | review-fork | —>
````

## SETTINGS.md

```markdown
# <Project name>

## Primary task
<one sentence>

## Lean bar
<smallest maintainable surface here>

## Non-goals
-

## Project creation
- Local parent path / Naming / New vs nest / Who creates remote / Visibility / Bootstrap:

## Architecture
-

## Project structure
-

## Source control
- Host / Remote / Visibility / Local path:

## Stack (and where used)
| Layer | Language / runtime | Libraries |
|-------|--------------------|-----------|
|       |                    |           |

## Similar-project choice
- continue | review-fork
```

## INDEX.md entries

```markdown
- [<slug>](projects/<slug>/SETTINGS.md) — <gist>; stack=<stack-slug>; status=<phase>
- [<title>](projects/<slug>/research/<file>.md) — stack=<stack-slug>; tags=…
```

## RAG habit

Before recommending libraries: read `INDEX.md` → matching `stacks/` + prior
`research/` → reuse what holds; re-research only missing/stale; note carries in
new `research/`.

## links.md

Filled at Create close-out. Shape and close-out: [handoff.md](handoff.md) § Write.
