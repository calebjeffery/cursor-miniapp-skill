# MiniApp register

Durable memory for every miniApp process. Later projects **RAG** this store
instead of rediscovering the same stack facts.

## Root

```
~/.agents/miniapp-register/
├── INDEX.md                 # Global RAG index (always update)
├── projects/
│   └── <slug>/
│       ├── SETTINGS.md      # Locked project settings
│       ├── CONTEXT.md       # Glossary (domain-modeling)
│       ├── STATUS.md        # Checklist phase + timestamps
│       ├── research/        # Cited stack / library research
│       ├── similar/         # Similar free-project finds
│       └── links.md         # Repo path, remote URL, handoff path
└── stacks/
    └── <stack-slug>/
        └── INDEX.md         # Cross-project notes for this stack
```

Expand `~` to the user's home directory. On this machine that is typically
`C:\Users\<user>\.agents\miniapp-register\`.

## Slug

Lowercase kebab-case from the project name (`family-os-planner`). If collision,
append a short year-month suffix (`family-os-planner-2026-09`).

## Write rules

1. **Single source of truth.** A decision lives in `SETTINGS.md` or one ADR —
   the index only gists and links.
2. **Update INDEX.md** whenever you add research or finish a phase.
3. **No secrets.** Remotes, paths, stack names — yes. Tokens, passwords — never.
4. **Cite.** Every research claim points at a primary URL or package page.

## SETTINGS.md template

```markdown
# <Project name>

## Primary task
<one sentence>

## Lean bar
<what "as little code as possible" means here>

## Non-goals
-

## Architecture
-

## Project structure
-

## Source control
- Host:
- Remote:
- Visibility:
- Local path:

## Stack (and where used)
| Layer | Language / runtime | Libraries |
|-------|--------------------|-----------|
|       |                    |           |

## Workflow confirmation
- User confirmed creation pipeline: yes/no
- Similar-project choice: continue | review-fork
```

## INDEX.md entry shape

Append under the matching section (Projects / Stacks / Research):

```markdown
- [<slug>](projects/<slug>/SETTINGS.md) — <one-line gist>; stack=<stack-slug>; status=<phase>
```

Research rows:

```markdown
- [<title>](projects/<slug>/research/<file>.md) — stack=<stack-slug>; tags=lib,pattern,…
```

## RAG habit

Before recommending libraries for a new miniApp:

1. Read `INDEX.md`
2. Open matching `stacks/<stack-slug>/` and prior `research/` files
3. Reuse what still holds; only re-research what is missing or stale
4. Note reuse in the new project's `research/` ("carried from `<slug>`")
