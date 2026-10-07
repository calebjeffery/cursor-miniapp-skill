# Research worker brief

Fill brackets from register `SETTINGS.md`; give this file to the subagent only.

---

## Mission

Smallest maintainable surface for this stack — thin libs/patterns, solid for growth.

## Project

- Slug: `<slug>`
- Primary task: `<primary task>`
- Architecture: `<architecture>`
- Structure: `<structure>`
- Stack table: `<paste stack rows>`
- Lean bar: `<lean bar>`
- Non-goals: `<non-goals>`

## Output paths

1. `~/.agents/miniapp-register/projects/<slug>/research/stack-libraries.md`
2. `~/.agents/miniapp-register/projects/<slug>/research/patterns-and-structures.md`
3. Update `~/.agents/miniapp-register/INDEX.md`
4. Upsert `~/.agents/miniapp-register/stacks/<stack-slug>/INDEX.md`

## Ranking (order)

1. **Small surface** — few APIs; thin wrappers over platform/runtime
2. **Maintained** — active upstream; clear permissive-leaning license
3. **SOLID fit** — clean dependency direction; swappable adapters
4. **Right data structures** — match access patterns; say why
5. **Named patterns** — only when they cut code or clarify seams
6. **Reuse** — stdlib / platform over a new dependency

## Prefer smaller defaults

| Temptation | Prefer |
|------------|--------|
| Kitchen-sink framework | Thin lib or stdlib for the one job |
| Abandoned package | Maintained alt or platform API |
| Second ORM / HTTP stack | The one in SETTINGS |
| Enterprise layer over runtime | Direct runtime feature |

## Method

- Primary sources only; cite URL + version or "as of `<date>`"
- ≤3 candidates per concern; one default + one escape hatch
- Prior register research for this stack: start there; extend gaps only

## patterns-and-structures.md must include

- Module/folder seams for chosen architecture
- Data structures for core entities (+ why)
- Lean patterns at stated scale
- **Defer until scale demands** — with explicit triggers

## Done means

- Both research files written and cited
- INDEX.md + stack shard updated
- Short "recommended default stack" summary at top of `stack-libraries.md`
