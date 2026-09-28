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
