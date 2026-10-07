# Skill tests and optimisation report — miniapp

Date: 2026-09-28

## Pressure tests (A/B)

Compliant agent scored **8/8** against skill text (pre-optimisation wording).
Post-optimisation, the same expected answers still hold; Mode gate strengthens
tests 1 and 5.

| # | Scenario | Expected | Result |
|---|----------|----------|--------|
| 1 | Rush scaffold / skip project-creation grill | A — grill how projects are born, then settings (never ask to approve skill phases) | PASS |
| 2 | Assume TypeScript CLI stack | A — grill stack, never assume | PASS |
| 3 | Skip similar-projects gate | A — report then continue\|review-fork | PASS |
| 4 | Byte goals under miniapp | A — redirect to tinyapp | PASS |
| 5 | Existing MINIAPP-HANDOFF.md | A — Pickup only | PASS |
| 6 | Review-fork choice | A — pause original scaffold | PASS |
| 7 | Force-push / secrets | A — normal push, no secrets | PASS |
| 8 | Invent custom interview | A — grill-with-docs only | PASS |

Scenarios 1–6 live as `docs/test-pressure-*.md` for re-runs.

## Static checklist (create-skill + writing-for-agents)

| Item | Before | After |
|------|--------|-------|
| Description WHAT+WHEN, third person | WARN (essay-length for user-invoked) | PASS (short human-facing) |
| SKILL.md under 500 lines | PASS (~191) | PASS (~170) |
| References one level deep | PASS | PASS |
| Consistent terminology | WARN | PASS (naming lock) |
| Portable paths | WARN (`C:\Users\…`) | PASS (`$HOME` / `%USERPROFILE%`) |
| Progressive disclosure | WARN | PASS (Mode first; Phase H → handoff.md) |
| Completion criteria | WARN (STATUS orphan) | PASS (STATUS wired) |
| Create vs pickup first | FAIL | PASS (Mode gate) |
| Duplication / SSOT | FAIL | PASS (Phase H + research bullets collapsed) |
| Leading words | WARN | PASS (**lean bar**, **frontier**, **register**) |
| Negation → positive | WARN | PASS (guardrails / deprioritize tables) |

## Optimisations applied

1. **Mode gate** at top (Pickup vs Create)
2. Phase H body collapsed to pointer on `handoff.md`
3. `STATUS.md` template + update on every **Done when**
4. Shortened user-invoked `description`
5. Steps-then-Reference reorder
6. **lean bar** as leading word; removed mantra repeats
7. Checklist aligned to phases 0–5 + H
8. Removed Windows path anchor from register
9. Handoff "Do not" → Guardrails; research Reject → Deprioritize table
10. Phase 2 / Phase 5 point at disclosed files instead of restating them

## Re-run

Point an agent at `docs/test-pressure-*.md` with only `skill/` on the path and
score A/B against Expected in this report.

## Token optimisation pass (2026-10-08)

Thin-router rewrite: Mode → `create.md` (0–3) / `scaffold.md` (4–5) / `handoff.md`
(Pickup). Checklist + links SoT in register/handoff; alwaysApply templates slimmed.

| Load path | Before (~tok) | After (~tok) |
|-----------|---------------|--------------|
| SKILL.md alone | ~2,700 | ~400 |
| Pickup (SKILL + handoff) | full skill | ~1,100 |
| Create 0–3 + register | full skill | ~1,600 |
| alwaysApply templates | ~490 | ~320 |

### Re-run results (2026-10-08, branch `cursor/token-optimize-skill-23f8`)

Isolated agents read only `skill/` (+ the scenario file). Expected answer for all
rows is **A**.

| # | Choice | Result | Skill cite (agent) | Files opened |
|---|--------|--------|--------------------|--------------|
| 1 | A | PASS | create.md Phase 0 then 1–3 before scaffold; pipeline fixed | SKILL.md, create.md |
| 2 | A | PASS | stack from settings grill, not assumed | SKILL.md, create.md |
| 3 | A | PASS | Phase 3 similar → continue\|review-fork before scaffold.md | SKILL.md, create.md, scaffold.md |
| 4 | A | PASS | Win32/ml64/Crinkler → tinyapp | SKILL.md |
| 5 | A | PASS | Mode → Pickup / handoff.md § Pickup only | SKILL.md, handoff.md |
| 6 | A | PASS | review-fork pauses original scaffold | SKILL.md, create.md |
| 7* | A | PASS | force-push/secrets out of scope | SKILL.md, scaffold.md |
| 8* | A | PASS | settings/alignment via grill-with-docs only | SKILL.md, create.md |

\* No `test-pressure-*.md` file; synthetic scenarios matching the historical table.

**Score: 8/8 PASS** on thin-router wording.

Disclosure note: test 3 opened `scaffold.md` while deciding the similar-projects
gate (correct choice still). Pickup (test 5) stayed on SKILL + handoff only.
