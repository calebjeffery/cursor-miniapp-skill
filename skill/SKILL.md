---
name: miniapp
description: >-
  Orchestrate a greenfield miniApp: grill project settings with docs, pick any
  language stack, research the leanest libraries (SOLID, small surface), index
  findings in the miniapp register for RAG, check free similar projects, scaffold
  structure + agentic setup, git init/push, then hand off for an alignment grill
  in the new repo. Use when the user says miniapp, miniApp, new mini project,
  stack-agnostic tiny app, or wants a lean greenfield scaffold not locked to
  Windows or tinyapp.
disable-model-invocation: true
---

# MiniApp — lean greenfield orchestrator

Spin up a **mini** project: as little code as possible, still maintainable and
scalable. Lineage is **tinyapp** (wrap the platform, one increment at a time,
measure cost) without locking to Windows or any one stack — the user chooses.

This skill **orchestrates**. It does not invent a parallel interview style:
settings and alignment grills run through Matt Pocock's **grill-with-docs**
(grilling + domain-modeling). Research runs as a **subagent**. Memory lives in
the **miniapp register** so later miniApps can RAG prior stack work.

## When this skill applies

- User says `miniapp`, `miniApp`, "lean greenfield", "tiny but any stack"
- New project creation where stack, remote, and architecture are still open

Redirect:
- Byte-obsessed native Win32 / ml64 / Crinkler → **tinyapp**
- Already inside a settled repo with a feature idea → **grill-with-docs** / main flow
- Fog too big for one session → **wayfinder**, then return here only for scaffold

## Hard constraints

- **Stack is chosen, not assumed.** Never default to Windows-only or a fixed language.
- **Lean surface.** Prefer the tiniest maintained libraries that still obey SOLID,
  clear data structures, and named design patterns. Reuse over rewrite.
- **Register every durable decision.** Settings, research, similar-project finds,
  and handoff pointers go in the miniapp register (see [register.md](register.md)).
- **No scaffold until settings are locked** and the user confirms the creation workflow.
- **Inform before inventing.** Surface free similar projects first; ask before cloning a review fork.

## Checklist

Copy and keep updated:

```
MiniApp progress:
- [ ] 0. Workflow clarified (how new projects are created here)
- [ ] 1. Register entry created; slug known
- [ ] 2. Settings grill done (arch, structure, VCS/remote, stack + where used)
- [ ] 3. Stack research worker done; indexed for RAG
- [ ] 4. Similar free projects reported; user chose continue | review-fork
- [ ] 5. Structure + agentic setup scaffolded; git init + remote push
- [ ] 6. User reviewed structure
- [ ] 7. Bare handoff written into the new project
```

## Phase 0 — Clarify the creation workflow

Before any settings questions, state the pipeline in one short block and get
explicit OK (or edits):

1. Grill project **settings** (architecture, structure, source control, stack)
2. Research **lean libraries** for that stack; write into the register RAG index
3. Search for **free similar projects**; offer a review-fork path
4. Scaffold **structure + agentic setup**; `git init` and push to the chosen remote
5. User reviews structure
6. Write a **bare handoff** so opening the new project starts an alignment grill
   that pulls register research and re-runs grill-with-docs

**Done when:** user confirms or amends this workflow. Do not skip.

## Phase 1 — Register + settings grill

1. Create a register entry (`~/.agents/miniapp-register/…`) per [register.md](register.md).
2. Run **grill-with-docs** (Skill tool: `grilling` + `domain-modeling`). Prefer a
   working directory that will hold early docs; if none exists yet, grill against
   the register project folder and copy glossary/ADRs into the repo at scaffold time.

Frontier must cover, in dependency order (one question per turn unless they ask
for the full frontier):

| Decision | Examples |
|----------|----------|
| Architecture patterns | ports/adapters, modular monolith, event-driven, MVC, etc. |
| Project structure | monorepo vs single package; folder conventions |
| Source control + remote | git host (GitHub / Gitea / GitLab / Cursor / local-only); repo name; visibility |
| Language stack + where used | languages, runtimes, frameworks — and which layer each belongs to (UI, API, data, scripts, CI) |

Also settle: primary task in one sentence, non-goals, and the **lean bar**
(what "as little code as possible" means for this project).

Persist every settled answer into the register `SETTINGS.md` and any
`CONTEXT.md` / ADRs as they crystallise.

**Done when:** frontier empty and user confirms shared understanding of settings.

## Phase 2 — Stack research worker

Dispatch a **subagent** (background if available; otherwise a tightly scoped
Task) with the brief in [research-brief.md](research-brief.md).

The worker must:

1. Prefer **primary sources** (official docs, package registries, source repos)
2. Rank candidates by **small surface** × **maintenance** × SOLID fit
3. Name relevant **data structures** and **design patterns** with justification
4. Write cited Markdown into the register project's `research/` and update the
   global RAG index (`INDEX.md` + stack shard)

While it runs, ask only frontier questions that do not depend on its output.

**Done when:** research files exist, index entries point at them, and you have
summarised the recommendation to the user for a quick confirm/amend.

## Phase 3 — Similar free projects

Research the web for **free-to-use** projects closest to the primary task + stack
(OSS license that allows use). Present findings **before** scaffolding:

- Name, license, URL, why it is similar, lean-vs-heavy note

Ask (one question):

- **Continue** creating this miniApp from scratch, or
- **Spin a review project** (second miniApp / clone path) to study the similar work first

If they pick review: create/register that review track, pause or fork this
checklist, and do not pretend the original scaffold is done.

**Done when:** user chose continue or review-fork and the choice is logged in the register.

## Phase 4 — Scaffold, agentic setup, git

Only after continue:

1. Create the project directory and **bare structure** matching settled settings
   (configs, folder skeleton, README stub — not feature code)
2. Agentic setup: run **setup-matt-pocock-skills** conventions where they fit
   (`CONTEXT.md`, `docs/adr/`, `AGENTS.md`/`CLAUDE.md` agent-skills block, issue
   tracker doc). Copy register glossary/ADRs into the repo.
3. Drop a pointer file `MINIAPP.md` in the repo root linking to the register slug
4. `git init` (if needed), initial commit of the skeleton, add remote, push —
   matching the user's remote choice. Never force-push; never commit secrets.
5. Ask the user to **review the structure**. Amend until they accept.

**Done when:** structure accepted, remote has the base commit (or local-only was chosen).

## Phase 5 — Bare project handoff

Write `MINIAPP-HANDOFF.md` in the new repo using [handoff.md](handoff.md).

Tell the user: open the new project in a fresh session and invoke **miniapp**
(or open with the handoff as the prompt). The pickup path is Phase H below.

**Done when:** handoff file is committed (or staged for the user) and they know
how to pick it up.

## Phase H — Handoff pickup (new project session)

When the user opens a miniApp project and this skill is invoked with an existing
`MINIAPP-HANDOFF.md` / register pointer:

1. Load register entry + RAG-relevant stack research from the index
2. Run **grill-with-docs** again to align the user with the miniApp's settled
   nature, stack choices, and lean bar
3. Re-assert: little code, reuse, SOLID, good data structures, design patterns,
   maintainable and scalable
4. Only after alignment, merge onto the main engineering flow
   (`to-spec` / `to-tickets` / `implement` as size demands)

**Done when:** frontier empty and user confirms alignment; then stop or hand to
the next skill they choose.

## Orchestration notes

- **Facts** (registry APIs, license text, whether a remote exists): look up or
  dispatch a subagent — do not ask the user.
- **Decisions**: always the user's; grill one frontier question at a time.
- If `AskQuestion` exists, use it for fixed-choice settings; otherwise use the
  grilling prose format.
- Keep register paths absolute and stable so other sessions can RAG them.

## Additional resources

- Register layout and write rules: [register.md](register.md)
- Research worker brief: [research-brief.md](research-brief.md)
- Handoff template + pickup: [handoff.md](handoff.md)
