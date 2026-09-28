# MiniApp handoff

## Write (end of creation)

Create `MINIAPP-HANDOFF.md` at the **new project root** (and keep a copy pointer
in the register `links.md`). This is a **bare** handoff: enough for a fresh
agent to start Phase H, not a dump of the whole chat.

```markdown
# MiniApp handoff — <project name>

## Pickup
Invoke the **miniapp** skill in this repo (Phase H). Do not scaffold again.

## Register
- Slug: `<slug>`
- Register root: `~/.agents/miniapp-register/projects/<slug>/`
- SETTINGS: `…/SETTINGS.md`
- Research: `…/research/`
- Global index: `~/.agents/miniapp-register/INDEX.md`

## Settled (gist only — details in register)
- Primary task:
- Architecture:
- Structure:
- Stack:
- Remote:

## Lean bar
<one paragraph>

## Suggested skills (in order)
1. miniapp (Phase H pickup)
2. grill-with-docs (alignment) — loads grilling + domain-modeling
3. After alignment: to-spec → to-tickets → implement (or implement alone if small)

## Do not
- Re-pick the stack unless the alignment grill overturns it
- Add dependencies not justified by register research
- Expand beyond the lean bar without an ADR
```

Also ensure repo-root `MINIAPP.md` exists:

```markdown
# MiniApp
Slug: `<slug>`
Register: `~/.agents/miniapp-register/projects/<slug>/`
Handoff: see `MINIAPP-HANDOFF.md`
```

Commit these with the skeleton when the user accepts structure.

## Pickup (Phase H)

1. Read `MINIAPP-HANDOFF.md` and register `SETTINGS.md`
2. RAG: open `INDEX.md`, then matching stack + this project's `research/`
3. Run grill-with-docs to align the user (architecture, seams, lean bar,
   first vertical slice) — decisions still belong to the user
4. Keep pushing **little code, reuse, SOLID, good data structures, design
   patterns, maintainable and scalable**
5. When frontier is empty and user confirms, stop or continue into the main
   engineering flow they choose
