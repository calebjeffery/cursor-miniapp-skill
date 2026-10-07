# How this Cursor skill was created

**miniapp** packages a greenfield orchestration process as a Cursor Agent Skill.

## Starting point

- **tinyapp** — Dave Plummer / Dave's Garage lean-app process (wrap the platform, one feature at a time, measure cost), packaged as a Cursor skill for Windows 11 Win32.
- **Matt Pocock skills** — `grill-with-docs`, `grilling`, `domain-modeling`, `research`, `handoff`, and the idea → ship main flow.

## What changed from tinyapp

| tinyapp | miniapp |
|---------|---------|
| Windows 11 + ml64 / Crinkler | Stack chosen by the user |
| Byte growth log | Lean bar + library surface |
| Single-app build loop | Multi-phase orchestrator + register RAG |
| No durable cross-project memory | `~/.agents/miniapp-register/` |

## Design choices

1. **User-invoked skill** (`disable-model-invocation: true`) — deliberate project creation, not ambient auto-fire.
2. **Progressive disclosure** — `SKILL.md` is a Create/Pickup router; Create phases live in `create.md` / `scaffold.md`; register, research brief, and handoff stay sibling files.
3. **Register outside the skill** — personal memory and RAG index must not ship inside the git skill repo.
4. **Reuse interview primitives** — do not invent a second grilling style; call Matt Pocock’s skills.
5. **Similar projects before scaffold** — inform and offer a review-fork path so free prior art is not ignored.

## Validation

- [x] SKILL.md under 500 lines
- [x] Description in third person with WHAT + WHEN
- [x] References one level deep from SKILL.md
- [x] No secrets or per-project register data in the repo
