# MiniApp Create — Phases 4–5

Only after Phase 3 **continue**. Register SoT: [register.md](register.md).
Handoff + close-out: [handoff.md](handoff.md).

## Phase 4 — Scaffold, agentic setup, git

1. Create project directory and **bare structure** from SETTINGS (configs, folder
   skeleton, README stub — not feature code).
2. Agentic setup where it fits (**setup-matt-pocock-skills**): `CONTEXT.md`,
   `docs/adr/`, `AGENTS.md`/`CLAUDE.md` agent-skills block, issue tracker doc.
   Copy register glossary/ADRs into the repo.
3. **Project rules (required):**
   - Copy [templates/grill-with-docs.mdc](templates/grill-with-docs.mdc) →
     `.cursor/rules/grill-with-docs.mdc`
   - Generate `.cursor/rules/project-settings.mdc` from register `SETTINGS.md`
     via [templates/project-settings.mdc](templates/project-settings.mdc) —
     fill every section. Both rules `alwaysApply: true`.
   - Under `## Agent skills` in `AGENTS.md` or `CLAUDE.md`:
     `Default interview: grill-with-docs. Project law: .cursor/rules/project-settings.mdc.`
4. Write root `MINIAPP.md` and register `links.md` per [handoff.md](handoff.md)
   § Write.
5. `git init` if needed, initial skeleton commit, add remote, push — matching
   remote choice. Force-push and secret commits are out of scope.
6. User **reviews structure**; amend until accepted.

**Done when:** structure accepted; both project rules exist and reflect SETTINGS;
remote has base commit (or local-only chosen).

## Phase 5 — Bare project handoff

Complete [handoff.md](handoff.md) § Write (handoff file, `MINIAPP.md`, `links.md`,
close-out links + open). Tell user: after opening, invoke **miniapp** in Pickup
mode.

**Done when:** handoff committed or staged; `links.md` has local + remote (or
local-only); closing message has clickable Markdown links; open attempted or
explicit fallback.
