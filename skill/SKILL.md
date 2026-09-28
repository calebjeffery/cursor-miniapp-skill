---
name: miniapp
description: >-
  Orchestrates lean, stack-agnostic greenfield miniApps (settings grill,
  register RAG, research, scaffold, handoff).
disable-model-invocation: true
---

# MiniApp — lean greenfield orchestrator

**Naming:** invoke `miniapp`; product concept **miniApp**; files `MINIAPP.md` /
`MINIAPP-HANDOFF.md`.

Spin up a **mini** project under a **lean bar**: smallest maintainable surface —
reuse, SOLID seams, explicit data structures and patterns at this scale. Lineage
is **tinyapp** (wrap the platform, one increment at a time) without locking to
Windows or any one stack — the user chooses.

This skill **orchestrates**. Settings and alignment grills run through
**grill-with-docs** (Skills: `grilling`, `domain-modeling`). Research runs as a
**subagent**. Memory lives in the **miniapp register** so later miniApps can RAG
prior stack work.

## Mode (run first)

1. **Pickup** — repo has `MINIAPP-HANDOFF.md` (or user opened for alignment) →
   follow [handoff.md](handoff.md) § Pickup only. Skip Phases 0–5.
2. **Create** — no handoff → run Phases 0–5 in order. Stop after Phase 5 unless
   the user asks for pickup in-session.

## Checklist

Create/update `~/.agents/miniapp-register/projects/<slug>/STATUS.md` from this
list after each phase (see [register.md](register.md)).

```
MiniApp progress:
- [ ] 0. Project-creation workflow clarified (where/how projects are born)
- [ ] 1. Register entry created; slug known
- [ ] 2. Settings grill done (arch, structure, VCS/remote, stack + where used)
- [ ] 3. Stack research worker done; indexed for RAG
- [ ] 4. Similar free projects reported; continue | review-fork chosen
- [ ] 5. Structure + agentic setup; git init/push; structure accepted; handoff written
- [ ] H. Pickup alignment (new session only)
```

## Phase 0 — Clarify the project-creation workflow

The miniApp skill phases are fixed — do **not** ask the user to approve or amend
this skill's pipeline. Phase 0 grills how **new projects are created** in the
user's world (facts you look up; decisions they own).

Grill the frontier (one question per turn unless they ask for the full frontier).
Look up what you can first (existing project roots, remotes, naming patterns):

| Decision | Examples |
|----------|----------|
| Local home for new projects | parent folder(s), machine-specific roots |
| Naming | kebab-case, org prefix, date suffix |
| New repo vs existing | always new remote, or nest under a monorepo / umbrella |
| Who creates the remote | agent via `gh`/`glab`/Gitea, or user creates and pastes URL |
| Default visibility | public / private / internal |
| Bootstrap habits | empty commit first, LICENSE/README stubs, default branch name |

Persist settled answers into register `SETTINGS.md` under **Project creation**.

**Done when:** frontier empty on how projects get created here; `STATUS.md` updated.

## Phase 1 — Register + settings grill

1. Create a register entry per [register.md](register.md).
2. Run **grill-with-docs**. Prefer a working directory that will hold early docs;
   if none exists yet, grill against the register project folder and copy
   glossary/ADRs into the repo at scaffold time.

Frontier must cover, in dependency order (one question per turn unless they ask
for the full frontier):

| Decision | Examples |
|----------|----------|
| Architecture patterns | ports/adapters, modular monolith, event-driven, MVC, etc. |
| Project structure | monorepo vs single package; folder conventions |
| Source control + remote | git host (GitHub / Gitea / GitLab / Cursor / local-only); repo name; visibility |
| Language stack + where used | languages, runtimes, frameworks — and which layer each belongs to (UI, API, data, scripts, CI) |

Also settle: primary task in one sentence, non-goals, and the **lean bar** for
this project.

Persist every settled answer into register `SETTINGS.md` and any `CONTEXT.md` /
ADRs as they crystallise.

**Done when:** frontier empty, user confirms shared understanding of settings;
`STATUS.md` updated.

## Phase 2 — Stack research worker

Dispatch a **subagent** (background if available; otherwise a tightly scoped
Task) with [research-brief.md](research-brief.md) (SETTINGS fields filled in).

While it runs, ask only frontier questions that do not depend on its output.

**Done when:** research files exist, index entries point at them, recommendation
summarised for user confirm/amend; `STATUS.md` updated.

## Phase 3 — Similar free projects

Research the web for **free-to-use** projects closest to the primary task + stack
(OSS license that allows use). Present findings **before** scaffolding:

- Name, license, URL, why it is similar, lean-vs-heavy note

Ask (one question):

- **Continue** creating this miniApp from scratch, or
- **Spin a review project** (second miniApp / clone path) to study the similar work first

If they pick review: create/register that review track, pause or fork this
checklist; original scaffold stays incomplete until they resume.

**Done when:** continue | review-fork logged in the register; `STATUS.md` updated.

## Phase 4 — Scaffold, agentic setup, git

Only after continue:

1. Create the project directory and **bare structure** matching settled settings
   (configs, folder skeleton, README stub — not feature code)
2. Agentic setup: **setup-matt-pocock-skills** conventions where they fit
   (`CONTEXT.md`, `docs/adr/`, `AGENTS.md`/`CLAUDE.md` agent-skills block, issue
   tracker doc). Copy register glossary/ADRs into the repo.
3. Write root `MINIAPP.md` and register `links.md` (see [handoff.md](handoff.md) § Write)
4. `git init` (if needed), initial commit of the skeleton, add remote, push —
   matching the user's remote choice. Force-push and secret commits are out of scope.
5. Ask the user to **review the structure**. Amend until they accept.

**Done when:** structure accepted, remote has the base commit (or local-only was
chosen); `STATUS.md` updated.

## Phase 5 — Bare project handoff

Write `MINIAPP-HANDOFF.md` and root `MINIAPP.md` per [handoff.md](handoff.md) § Write.
Record final paths in register `links.md`.

### Close-out (required)

Creation is incomplete until the user can reach the project. Always:

1. Resolve from `links.md` / git remote: **remote URL** (HTTPS page or clone URL) and
   **absolute local path**
2. Put both in the closing message as clickable Markdown links (file URL or path for
   local; https for remote)
3. **Open** when the harness allows it — prefer opening the project folder in the
   editor; also open the remote project page in the browser when a remote exists
4. If open is unavailable, still print the links and say how to open them

Local-only projects: open/show the local path. Remote projects: show **both**
remote URL and local path, and open both when possible.

Tell the user: after opening, invoke **miniapp** in Pickup mode.

**Done when:** handoff committed or staged; `links.md` has local + remote (or
local-only); closing message shows those URLs; open attempted or explicit fallback;
`STATUS.md` updated.

## Phase H — Handoff pickup

Execute only in **Pickup** mode. Steps and completion: [handoff.md](handoff.md) § Pickup.

## Reference

### When this skill applies

- User says `miniapp`, `miniApp`, "lean greenfield", "tiny but any stack"
- New project creation where stack, remote, and architecture are still open

Redirect:

- Byte-obsessed native Win32 / ml64 / Crinkler → **tinyapp**
- Already inside a settled repo with a feature idea → **grill-with-docs** / main flow
- Fog too big for one session → **wayfinder**, then return here only for scaffold

### Hard constraints

- **Stack is chosen in the settings grill**, not assumed.
- Honour the **lean bar** from SETTINGS (reuse over rewrite; thin maintained libs).
- **Register every durable decision** (see [register.md](register.md)).
- **Scaffold only after** project-creation workflow (Phase 0) and settings (Phase 1) are locked.
- **Inform before inventing** — surface free similar projects first; ask before a review fork.
- **Close-out with access** — when Create finishes, always show (and open when possible)
  the updated project's remote URL and/or local path; never end on handoff text alone.

### Orchestration notes

- **Facts** (registry APIs, license text, whether a remote exists): look up or
  dispatch a subagent.
- **Decisions**: always the user's; grill one frontier question at a time.
- If `AskQuestion` exists, use it for fixed-choice settings; otherwise use the
  grilling prose format.
- Keep register paths absolute and stable so other sessions can RAG them.

### Additional resources

- Register layout and write rules: [register.md](register.md)
- Research worker brief: [research-brief.md](research-brief.md)
- Handoff template + pickup: [handoff.md](handoff.md)
