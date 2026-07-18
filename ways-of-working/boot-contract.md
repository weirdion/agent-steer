# The Boot Contract

A fresh or compacted agent session must be able to pick up cleanly — orient in the project, know what just happened, and continue without the operator re-explaining. That only works if every project exposes its durable knowledge in a **defined read order**, and the agent honors it before acting.

This is the shape a project's own boot sequence inherits from the steer. A project states only what's *local* to it (which files it has, what's specific to it); the *shape* comes from here.

## The read order

Read before doing, not after. A well-formed sequence goes from *what/why* to *how* to *now*:

1. **The steer** — this repo. Load the spine; pull ways-of-working and preferences on relevance.
2. **What the project is and why** — its vision/purpose. What it's for, what it deliberately isn't (yet).
3. **How it's built** — its architecture and the structural decisions that shape everything else.
4. **The rules that are load-bearing here** — the project's own conventions, especially the ones marked as overrides or local scars. These are rules, not suggestions; they exist because something drifted without them.
5. **What's already been decided** — the decisions log, so settled questions aren't re-debated.
6. **What's deferred** — the backlog of scoped-but-not-built work, so you don't re-scope something already parked.
7. **What just happened and where we left off** — the live-state log, read from the top. This carries the active work and the next step.
8. **What's unverified** — anything shipped or designed that still needs hands-on confirmation the agent couldn't perform.

Not every project has all eight. A thin project may collapse several into one file. The order is the invariant; the file count is a derivation. See [knowledge-layers.md](knowledge-layers.md) for what each of these *is* and where it lives.

## Index before you read

A project's context should be *indexed* — a short table, one line per topic with a description — so the agent reads the relevant topic, not the whole corpus. The index is loaded; the topics are pulled on relevance. This is the same discipline the steer applies to itself: it's what lets the practice scale to a large project or a fleet of them without the boot sequence becoming a wall of text nobody fully ingests.

## Session start, session end

- **Start:** follow the read order. If the operator names a specific task, load the topics that task touches; you don't have to read everything every time, but you do have to read the top-of-log live state so you know where things stand.
- **End:** append one brief entry to the live-state log — what was done, where it stands, the next step. This is the handoff to the next session (which may be a compacted *you*). Keep it tight; link to context updates rather than restating them.

*Why this contract exists:* runtimes are disposable and context windows compact. The project's `.agents/` — not the agent's memory of the conversation — is what persists. If the boot contract is honored, any fresh session is as oriented as the last one. If it's skipped, the agent re-derives from scratch, re-asks answered questions, and re-litigates settled decisions. The read order is cheap; the re-derivation is not.
