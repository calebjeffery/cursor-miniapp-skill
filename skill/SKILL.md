---
name: miniapp
description: >-
  Lean greenfield miniApp orchestrator (settings grill, register RAG, research,
  scaffold, handoff). User-invoked only.
disable-model-invocation: true
---

# MiniApp

Orchestrates a **miniApp**: smallest maintainable surface, stack chosen in grill,
memory in the **register** for later RAG. Invoke `miniapp`; files `MINIAPP.md` /
`MINIAPP-HANDOFF.md`.

## Mode (run first)

1. **Pickup** — repo has `MINIAPP-HANDOFF.md` (or user opened for alignment) →
   [handoff.md](handoff.md) § Pickup only.
2. **Create** — no handoff → [create.md](create.md) Phases 0–3, then
   [scaffold.md](scaffold.md) Phases 4–5. Stop after 5 unless user asks for Pickup
   in-session.

## Global rules

- **Decisions** are the user's; grill **one frontier question per turn** (full
  frontier only if they ask). Use `AskQuestion` for fixed choices when available.
- **Facts** (remotes, licenses, registry): look up or dispatch a subagent.
- **Stack** comes from the settings grill; honour the **lean bar** in SETTINGS.
- Byte-obsessed native Win32 / ml64 / Crinkler → **tinyapp** (not this skill).
- After every phase: update register `STATUS.md` (checkbox + timestamp) per
  [register.md](register.md).
- Register every durable decision; paths absolute and stable for RAG.
- Create close-out: clickable `https://` + `file:///` links (and open when
  possible) — details in [handoff.md](handoff.md) § Write.

## Progress

Checklist SoT: register `STATUS.md` template in [register.md](register.md).
Create/update `~/.agents/miniapp-register/projects/<slug>/STATUS.md` each phase.
