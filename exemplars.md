# Exemplars

The best way to understand a principle is to see it *realized*. This file describes what the practice looks like when it's working — as pattern illustrations, not as templates to copy, and not as pointers to specific repositories (this repo is public; the projects that realize the practice are not).

**Read these as "here's the invariant, realized," not "here's a file to clone."** The value is the shape and the reasoning; the specifics belong to whatever project you're actually in.

## What a mature adopted project looks like

- **A thin local layer over the steer.** The project's boot sequence points at the steer, then lists only its own files. Its conventions doc is short — it holds the project's earned scars (marked LOCAL / OVERRIDE with reasons), not a restatement of universal principles. The commons come from the steer; the project carries its story.

- **Load-bearing rules that name their scar.** The strongest project rules read "this is a rule *because* X happened without it." A convention that drifted and caused a specific pain, now written as a rule so it can't drift again. That reasoning is what makes the rule believed and correctly applied — and it's exactly the kind of scar that stays *local* (the steer holds universal invariants; the specific drift that earned a rule belongs to the project that lived it).

- **A self-correcting live-state log.** The top entry is the current handoff. When a past diagnosis proved wrong, it's marked superseded and kept — with a pointer to what's correct now — so the record of ruled-out paths survives. Especially valuable where the work is diagnostic: the log reads as "here's what we eliminated and why," not just "here's the answer."

- **A needs-verification checklist that's actually used.** Where the agent can't run the thing, shipped work lands on a checklist marked untested / verified / partial, and "done" is reserved for what's been confirmed. The gap between shipped and verified is visible instead of assumed away.

- **Deferrals captured at the moment of deferral.** The backlog holds scoped-but-unbuilt work, each with why it's deferred and what pulls it forward — written when the punt happened, not reconstructed later from commit messages.

## The parallel-agent pattern (for projects that need it)

Some projects host more than one kind of agent work — for example, an engineering track and a separate creative or operational track — with different rhythms and different tolerances for rigor. The pattern that works: **give each track its own boot sequence and its own durable layers, cleanly separated, each pointing at the steer for the commons.** The engineering track leans on the full rigor; a creative or exploratory track may run looser ("guidelines, not rules; log what you tried and what failed") — but both inherit the spine and the knowledge-layer discipline. The separation is deliberate: the tracks don't bleed idioms into each other.

This is a *composition* of the invariants, not a different practice. The fleet case (many repos, shared operational playbooks, per-project context, role-specialized agents) is the same move at larger scale: apply the invariants per unit, then compose with a shared layer. If a multi-agent or multi-repo setup *doesn't* reduce to "invariants + composition," that's a signal to look for accidental complexity, or a missing invariant.

## How to use this file

When you're unsure what a layer should look like in practice, come here for the shape, then build the version that fits the project you're in. If you find yourself copying an exemplar's specifics rather than its shape, stop — the specifics were that project's scars, not yours.
