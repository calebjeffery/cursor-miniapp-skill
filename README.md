# Cursor MiniApp Skill

A [Cursor Agent Skill](https://cursor.com/docs/agent/skills) that **orchestrates lean greenfield projects**: grill settings with docs, pick any language stack, research the smallest maintainable libraries, index findings in a durable **miniapp register** for RAG, surface free similar projects, scaffold structure + agentic setup, then hand off into an alignment grill in the new repo.

Lineage is [tinyapp](https://github.com/calebjeffery/cursor-tinyapp-skill) (minimal surface, one increment at a time) without locking to Windows or a fixed stack. Settings and alignment interviews use Matt Pocock’s [grill-with-docs](https://github.com/mattpocock/skills) flow (`grilling` + `domain-modeling`).

## What this skill does

1. Clarifies the **new-project creation workflow**
2. Grills **architecture, project structure, source control/remote, and language stack** (and where each layer is used)
3. Stores memory in `~/.agents/miniapp-register/` for later RAG
4. Dispatches a **research worker** for lean libraries (SOLID, data structures, design patterns, little code)
5. Reports **free similar projects** before inventing; optional review-fork path
6. Scaffolds structure + agentic setup, `git init`, push to remote
7. Writes a **bare handoff** so opening the new project runs Phase H alignment

## Install

### Agents skills directory (recommended if you use Matt Pocock skills)

```powershell
# Windows
Copy-Item -Recurse -Force ".\skill" "$env:USERPROFILE\.agents\skills\miniapp"
```

```bash
# macOS / Linux
cp -r skill ~/.agents/skills/miniapp
```

### Cursor personal skills

```powershell
Copy-Item -Recurse -Force ".\skill" "$env:USERPROFILE\.cursor\skills\miniapp"
```

```bash
cp -r skill ~/.cursor/skills/miniapp
```

Invoke with **`/miniapp`**, or by mentioning miniApp / lean greenfield / stack-agnostic tiny app.

The register is created on first run at `~/.agents/miniapp-register/` (not shipped in this repo — it holds your project memory).

## Prerequisites

- Cursor (or compatible agent harness) with skills enabled
- Matt Pocock engineering skills recommended: `grill-with-docs`, `grilling`, `domain-modeling`, `setup-matt-pocock-skills`, `research`
- `gh` / git for remotes the user chooses during the grill

## Repository layout

```
cursor-miniapp-skill/
├── README.md
├── LICENSE
├── skill/
│   ├── SKILL.md           # Orchestrator
│   ├── register.md        # Register + RAG rules
│   ├── research-brief.md  # Subagent research brief
│   ├── handoff.md         # Handoff template + Phase H
│   └── agents/
│       └── openai.yaml
│   └── templates/
│       └── grill-with-docs.mdc
└── docs/
    └── CREATION-PROCESS.md
```

## Related

- [cursor-tinyapp-skill](https://github.com/calebjeffery/cursor-tinyapp-skill) — Win32 / ml64 size-obsessed track
- [mattpocock/skills](https://github.com/mattpocock/skills) — grill-with-docs and engineering flow

## Skill tests

Pressure tests and optimisation notes: [docs/SKILL-TESTS.md](docs/SKILL-TESTS.md).

## License

MIT — see [LICENSE](LICENSE).
