# Adopting a New Project

Scaffolding a fresh repo into the practice. Because the steer carries the commons, a new project inherits almost the entire way of working by writing very little — it states only what's true about *itself*.

## The goal

Stand up a project `.agents/` that: points at the steer, captures what *this* project is, and gives a fresh session a clean boot. Not more. Resist the urge to pre-write rules the project hasn't earned yet — a new project has no scars, so it should have almost no OVERRIDE content. Its rules will accrete as it drifts and gets corrected.

## Steps

1. **Add the steer pointer.** The first item in the project's read-first sequence points at the steer's `INDEX.md`: load the spine, pull ways-of-working and preferences on relevance, then read the local files (which state only divergence). See [override-convention.md](override-convention.md).

2. **Write the "what and why."** A short vision/purpose: what this project is for, what it deliberately isn't (yet), what problem it solves. This is the one thing the steer can't supply — it's the project's identity.

3. **Sketch the architecture, lightly.** Even a few lines: the shape, the major pieces, the structural decisions already made. Expand as the structure firms up. Don't over-specify a design that hasn't been built.

4. **Create the durable-vs-live scaffold.** A context index (even with one or two topics), a decisions log (seed it with the founding choices and *why* — stack, structure, anything already settled), a backlog (for scoped-but-unbuilt work), and a live-state log (for the session handoff). These can start nearly empty; what matters is that the homes exist so knowledge lands in the right layer from day one. See [../ways-of-working/knowledge-layers.md](../ways-of-working/knowledge-layers.md).

5. **Add project-specific homes only as needed.** A needs-verification checklist if the agent won't be able to run the thing. A memory dir when the first behavior-shaping lesson appears — not before. Don't create empty ceremony.

6. **State the load-bearing local rules — only the real ones.** If the project has a genuine, known constraint from the start (a hard security boundary, a specific convention the operator insists on), write it as LOCAL with its *why*. If it doesn't, write nothing — the spine and ways-of-working already cover the defaults.

## What "done" looks like

A fresh session can read the steer, then the project's `.agents/`, and know: what this is, how it's shaped, what's decided, what's deferred, and where work stands. If that boot works, the scaffold is complete. Everything else the project earns as it grows.

*Why start thin:* a new project loaded up with inherited-looking rules it never earned is cargo cult — nobody believes rules that don't trace to a scar. Start with identity and the empty homes; let the specifics accrete from real experience. The steer supplies the discipline; the project supplies the story, over time.
