# Research worker brief

Give this brief to the subagent / background researcher. Fill the bracketed
fields from the register `SETTINGS.md` before dispatch.

---

## Mission

Find the **smallest maintainable surface** for this miniApp's stack — libraries
and patterns that keep code volume low while staying solid for growth.

## Project

- Slug: `<slug>`
- Primary task: `<primary task>`
- Architecture: `<architecture>`
- Structure: `<structure>`
- Stack table: `<paste stack rows>`
- Lean bar: `<lean bar>`
- Non-goals: `<non-goals>`

## Output paths (write these files)

1. `~/.agents/miniapp-register/projects/<slug>/research/stack-libraries.md`
2. `~/.agents/miniapp-register/projects/<slug>/research/patterns-and-structures.md`
3. Update `~/.agents/miniapp-register/INDEX.md` with links + tags
4. Upsert `~/.agents/miniapp-register/stacks/<stack-slug>/INDEX.md` with a short
   cross-project note

## Ranking criteria (in order)

1. **Small surface** — few APIs to learn; thin wrappers over the platform/runtime
2. **Maintained** — active upstream, clear license (prefer permissive OSS)
3. **SOLID fit** — dependency direction stays clean; easy to swap adapters
4. **Right data structures** — pick structures that match access patterns; say why
5. **Named patterns** — only when they reduce code or clarify seams (ports/adapters,
   strategy, repository, etc.)
6. **Reuse** — prefer stdlib / existing platform capability over a new dependency

Reject: kitchen-sink frameworks, abandoned packages, "enterprise" layers that
duplicate what the runtime already provides, second ORMs, duplicate HTTP stacks.

## Method

- Primary sources only (official docs, GitHub/source, package registry pages)
- Cite every recommendation with URL + version or "as of `<date>`"
- Compare at most 3 candidates per concern; pick one default + one escape hatch
- If a prior register research file covers this stack, **start there** and only
  extend what is missing

## patterns-and-structures.md must include

- Recommended module/folder seams matching the chosen architecture
- Data structures for the core domain entities (and why)
- Patterns that keep the codebase lean at the stated scale
- Explicit "do not introduce yet" list (premature abstractions)

## Done means

- Both research files written and cited
- INDEX.md and stack shard updated
- One short "recommended default stack" summary at the top of `stack-libraries.md`
  the orchestrator can read aloud to the user
