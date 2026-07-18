# Memory Discipline

Memory is the narrowest knowledge layer and the easiest to abuse. Kept disciplined, it's the agent's record of *how to work with this operator and this project* that no doc captures. Left loose, it becomes a second, stale copy of the docs.

## What memory is for

Memory holds **behavior-shaping context that is not documented elsewhere**:

- A correction: the operator said "not that, do this" — save what to avoid, and the reason.
- A confirmed non-obvious choice: "yes, that was right" — save it so future sessions don't drift away from a validated approach.
- A working-agreement rule or preference the operator stated.
- A lesson from an incident: a mistake that cost a cycle, so it isn't repeated.

## What memory is NOT for

- **Facts already in the docs.** What the project is, its architecture, current work, decisions — those live in their layers (see [knowledge-layers.md](knowledge-layers.md)). Update the doc, not memory.
- **Task-in-flight state.** That's live state, not memory.
- **Anything derivable from the code or the history.** If `git log` or the source already says it, don't restate it.

*Why the hard line:* memory that duplicates docs goes stale independently, and then two sources disagree. A wrong memory is worse than no memory — it actively misleads. Keep memory to the things that have no other home.

## Format and index

- One fact per file, with frontmatter (a slug, a one-line description used to judge relevance, a type).
- The body states the rule, then a *why* and a *how to apply*, so a future session can judge edge cases rather than pattern-match.
- Index each entry with one line and a *when to load* hook. Scan the index on start; load an entry only when its hook matches. Never put memory content in the index — it's a pointer.
- **Correct or delete stale memory the moment you notice it.** A memory that contradicts current code or a newer decision gets fixed in the same turn.

## The project-or-operator test — and promotion to the steer

Before writing a memory, ask: **is this lesson about *this project*, or about *the operator*?**

- **About the project** — a gotcha specific to this stack, this repo's history, this codebase's shape. → Local memory. It belongs to this project and shouldn't leak elsewhere.
- **About the operator** — a preference or working style that would hold in *any* project ("surface options with a recommendation, then build"; "keep commit messages tight"). → This is a candidate for the steer's [preferences](../preferences/collaboration.md). Raise it: "this seems like a general preference, not project-specific — worth promoting to the steer?" On confirmation, it moves up, where every project inherits it, and it stops being re-learned per repo.

*Why the test exists:* without it, operator-level preferences get rediscovered and rewritten in each project's memory, and the steer never accumulates them. The test is the flow that lets the steer *grow* from lived experience instead of only being edited by hand — the agent gains a scar in one project, and if it's a scar about *how the operator works*, it becomes part of the practice everywhere.

## Redaction — hard rule

Memory is in git. Project memory: no secrets, no credentials, no personal detail beyond what the project already exposes. Anything promoted to the steer is **public and project-agnostic** — no project names, no stacks, no machines, no paths, no personal specifics. Guidance-level content is safe; identifying detail is not. When in doubt, state the principle without the instance.
