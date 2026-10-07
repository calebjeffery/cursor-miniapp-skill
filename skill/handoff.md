# MiniApp handoff

## Write (end of creation)

Bare handoff at project root + register `links.md` — enough for Pickup, not a
chat dump.

### links.md

```markdown
# Links — <slug>

- Local path: `<absolute path>`
- Remote URL: `<https project page or — if local-only>`
- Clone URL: `<git@… or https://….git or —>`
- Handoff: `<absolute path to MINIAPP-HANDOFF.md>`
```

### Close-out (required)

Resolve remote URL + absolute local path from `links.md` / git. Emit **clickable
Markdown links** (not backtick-only paths); open project folder (and remote page
when remote exists) when the harness allows:

```markdown
- Repo: [project on GitHub](https://github.com/org/repo)
- Local: [open folder](file:///P:/Projects/repo)
- Handoff: [MINIAPP-HANDOFF.md](file:///P:/Projects/repo/MINIAPP-HANDOFF.md)
```

Use `https://` for remotes and `file:///` (forward slashes) for local. Local-only:
local + handoff links. Remote: remote + local + handoff.

### MINIAPP-HANDOFF.md

```markdown
# MiniApp handoff — <project name>

## Pickup
Invoke **miniapp** (Pickup mode). Alignment only; scaffold is done.

## Register
- Slug: `<slug>`
- Register root: `~/.agents/miniapp-register/projects/<slug>/`
- SETTINGS / Research / Global index: under that root; `INDEX.md` at register root

## Settled (gist — details in register)
- Primary task / Architecture / Structure / Stack / Local / Remote:

## Lean bar
<one paragraph from SETTINGS>

## Suggested skills
1. miniapp (Pickup) — this session
2. grill-with-docs — alignment, then standing default
3. to-spec → to-tickets → implement (or implement alone if small)

## Guardrails
- Stack/deps follow register research, ADRs, `.cursor/rules/project-settings.mdc`
  unless alignment grill changes them
- Scope past lean bar only via ADR
- If project-settings.mdc missing/drifts, regenerate from register SETTINGS first
```

### MINIAPP.md (repo root)

```markdown
# MiniApp
Slug: `<slug>`
Local: `<absolute path>`
Remote: `<https URL or local-only>`
Register: `~/.agents/miniapp-register/projects/<slug>/`
Handoff: see `MINIAPP-HANDOFF.md`
```

Commit with skeleton when structure is accepted.

## Pickup (Phase H)

1. Read `MINIAPP-HANDOFF.md` and register `SETTINGS.md`
2. RAG: `INDEX.md`, then matching stack + this project's `research/`
3. grill-with-docs for alignment (architecture, seams, lean bar, first vertical
   slice) — user owns decisions
4. Re-state lean bar; re-litigate stack only if grill overturns it
5. Frontier empty + user confirms → stop or continue into their chosen flow

**Done when:** alignment confirmed; update register `STATUS.md` checkbox H.
