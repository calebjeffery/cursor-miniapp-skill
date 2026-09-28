# MiniApp handoff

## Write (end of creation)

Create `MINIAPP-HANDOFF.md` at the **new project root** and record paths in
register `links.md`. This is a **bare** handoff: enough for a fresh agent to
start Pickup, not a dump of the whole chat.

### links.md (required at close-out)

```markdown
# Links — <slug>

- Local path: `<absolute path>`
- Remote URL: `<https project page or — if local-only>`
- Clone URL: `<git@… or https://….git or —>`
- Handoff: `<absolute path to MINIAPP-HANDOFF.md>`
```

After writing the handoff, the orchestrator **must** surface these links in the
closing message and open the project (editor folder + remote page when present)
per SKILL.md Phase 5 Close-out.

```markdown
# MiniApp handoff — <project name>

## Pickup
Invoke the **miniapp** skill in this repo (Pickup mode). Stay on alignment;
scaffold is already done.

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
- Local path:
- Remote URL:

## Lean bar
<one paragraph from SETTINGS>

## Suggested skills (in order)
1. miniapp (Pickup)
2. grill-with-docs (alignment) — loads grilling + domain-modeling
3. After alignment: to-spec → to-tickets → implement (or implement alone if small)

## Guardrails
- Keep stack and dependencies aligned with register research and ADRs unless
  the alignment grill explicitly changes them
- Expand scope beyond the lean bar only via ADR
```

Also ensure repo-root `MINIAPP.md` exists:

```markdown
# MiniApp
Slug: `<slug>`
Local: `<absolute path>`
Remote: `<https URL or local-only>`
Register: `~/.agents/miniapp-register/projects/<slug>/`
Handoff: see `MINIAPP-HANDOFF.md`
```

Commit these with the skeleton when the user accepts structure.

## Pickup (Phase H)

1. Read `MINIAPP-HANDOFF.md` and register `SETTINGS.md`
2. RAG: open `INDEX.md`, then matching stack + this project's `research/`
3. Run grill-with-docs to align the user (architecture, seams, lean bar,
   first vertical slice) — decisions still belong to the user
4. Re-state the **lean bar** from SETTINGS; re-litigate stack only if the grill
   overturns it
5. When frontier is empty and user confirms, stop or continue into the main
   engineering flow they choose

**Done when:** grill frontier empty, user confirms alignment; then stop or hand
off to the flow they choose (see Suggested skills). Update register `STATUS.md`
checkbox H.
