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

Resolve `~` via the environment home directory (`$HOME` / `%USERPROFILE%`); do
not hardcode OS-specific paths in new entries.

## Slug

Lowercase kebab-case from the project name (`family-os-planner`). If collision,
append a short year-month suffix (`family-os-planner-2026-09`).

## Write rules

1. **Single source of truth.** A decision lives in `SETTINGS.md` or one ADR —
   the index only gists and links.
2. **Update INDEX.md** whenever you add research or finish a phase.
3. **Update STATUS.md** after every phase (timestamp + checkbox).
4. **No secrets.** Remotes, paths, stack names — yes. Tokens, passwords — never.
5. **Cite.** Every research claim points at a primary URL or package page.

## STATUS.md template

```markdown
# Status — <slug>

Updated: <ISO-8601>

```
MiniApp progress:
- [ ] 0. Workflow clarified
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
```

## SETTINGS.md template

```markdown
# <Project name>

## Primary task
<one sentence>

## Lean bar
<what "smallest maintainable surface" means here>

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
