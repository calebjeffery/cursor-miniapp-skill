# MiniApp Create — Phases 0–3

Pipeline is fixed; do not ask the user to amend it. When Phase 3 settles on
**continue**, open [scaffold.md](scaffold.md). On **review-fork**, register that
track and pause this checklist.

Settings/alignment grills: **grill-with-docs** (`grilling` + `domain-modeling`).

## Phase 0 — Project-creation workflow

How **new projects are born** here (lookup first: roots, remotes, naming).

Frontier: local home · naming · new remote vs nest/monorepo · who creates remote
· default visibility · bootstrap habits (empty commit, LICENSE/README, default
branch).

Persist → register `SETTINGS.md` **Project creation**.

**Done when:** frontier empty on project creation.

## Phase 1 — Register + settings grill

1. Create register entry per [register.md](register.md).
2. Run **grill-with-docs**. Prefer a future-docs working dir; else grill in the
   register project folder and copy glossary/ADRs at scaffold.

Frontier (dependency order): architecture · project structure · source control +
remote · language stack + which layer each belongs to (UI, API, data, scripts,
CI) · primary task (one sentence) · non-goals · **lean bar**.

Persist → `SETTINGS.md` and any `CONTEXT.md` / ADRs as they crystallise.

**Done when:** frontier empty; user confirms shared understanding of settings.

## Phase 2 — Stack research worker

Fill [research-brief.md](research-brief.md) from SETTINGS; dispatch a subagent
(background if available) with that brief only.

While it runs, ask only frontier questions that do not depend on its output.

**Done when:** research files exist, index entries point at them, recommendation
summarised for user confirm/amend.

## Phase 3 — Similar free projects

Web-find **free-to-use** projects closest to primary task + stack. Present before
scaffold: name, license, URL, similarity, lean-vs-heavy note.

Ask once: **continue** from scratch, or **spin a review project** to study a
similar first.

Log choice in register. If review-fork: create/register that track; original
scaffold stays incomplete until resume.

**Done when:** continue | review-fork logged.

## Next

**continue** → [scaffold.md](scaffold.md).
