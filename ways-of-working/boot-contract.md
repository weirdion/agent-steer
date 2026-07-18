# The Boot Contract

A fresh or compacted agent session must be able to pick up cleanly — orient in the project, know what just happened, and continue without the operator re-explaining. That only works if every project exposes its durable knowledge in a discoverable place and the agent reads it before acting.

This is the *reading intent* a project's own boot sequence inherits from the steer. A project states only what's *local* to it (which files it has, what's specific to it); the sense-making progression comes from here.

## The reading intent, not a rigid sequence

Read before doing, not after. The intent is a progression from *what/why* → *how* → *now*:

- **The steer** — this repo. Load the spine; pull ways-of-working and preferences on relevance.
- **What the project is and why** — its vision/purpose. What it's for, what it deliberately isn't (yet).
- **How it's built** — its architecture and the structural decisions that shape everything else.
- **The rules that are load-bearing here** — the project's own conventions, especially the ones marked as overrides or local scars. Rules, not suggestions; they exist because something drifted without them.
- **What's already been decided** — the decisions log, so settled questions aren't re-debated.
- **What's deferred** — the backlog of scoped-but-not-built work, so you don't re-scope something already parked.
- **What just happened and where we left off** — the live-state log, read from the top. This carries the active work and the next step.
- **What's unverified** — anything shipped or designed that still needs hands-on confirmation the agent couldn't perform.

**This is a guiding light, not a checklist to execute verbatim.** A project may collapse several of these into one file, reorder them to fit how it actually thinks, or make some **conditional** — read only when the task calls for them. Conditional, task-triggered reads are first-class, not an exception: *"read the design system only when the task touches UI"* is a well-formed boot step, and often better than forcing every session through everything. The *progression* is the invariant; the exact order, the file count, and which reads are conditional are derivations the agent proposes from the project's shape and the operator ratifies (see the two-altitude principle in the README).

When a project's natural boot differs from this progression, the agent recommends the adjusted order and confirms it — it neither forces the steer's sequence nor silently diverges. See [knowledge-layers.md](knowledge-layers.md) for what each of these *is* and where it lives.

## Index before you read

A project's context should be *indexed* — a short table, one line per topic with a description — so the agent reads the relevant topic, not the whole corpus. The index is loaded; the topics are pulled on relevance. This is the same discipline the steer applies to itself: it's what lets the practice scale to a large project or a fleet of them without the boot sequence becoming a wall of text nobody fully ingests.

## Where the knowledge lives — proposed, not prescribed

The steer does **not** dictate the name of the agent directory or how the knowledge is physically arranged. That is structure — advisory, derived from the repo, proposed by the agent, ratified by the operator (README two-altitude principle). What the steer requires is only that the reading intent above has *a discoverable home* and *a pointer to the steer*. The criteria for proposing an arrangement:

- **One agent context, or several?** A single agent directory holds until the workspace grows large enough that one agent can't hold the cross-context. The deciding factor is **coupling, not size**: when a decision in one sub-domain forces decisions in the others, keep it unified — the agent needs the whole picture. When sub-domains are independent enough that separate agents won't starve each other of context, split by *purpose* (a directory per role) with a **shared layer** for the genuine commons — cross-cutting playbooks, per-project context that several roles consume. A tightly-coupled repo stays unified even when it's sizeable; an independent multi-domain workspace splits even when each part is small.
- **Naming is arbitrary; discoverability is not.** Whatever the directory is called, the pointer to the steer and the reading intent must be findable. The steer blesses no specific name.
- **Human-facing vs agent-facing knowledge is a real placement axis.** A project may deliberately keep agent-facing docs in the human documentation tree (so humans read them too) and keep the agent directory thin, or keep everything together. Both are legitimate; it's a choice the agent proposes from how the project treats its docs, not a default the steer imposes.

## Tool-agnostic body, thin per-tool entrypoint

The practice is independent of which coding agent reads it. Different tools have different entrypoint conventions — a root instructions file, a tool-specific config directory, a spec format, a pasted system prompt. Keep the knowledge in **one tool-agnostic body** (the agent directory), and give each tool a **thin entrypoint that points at it** rather than duplicating content into each tool's native format.

*Why:* the same project is often worked by more than one agent, and tools change. Duplicating the knowledge into every tool's format guarantees drift — the copies diverge and no one knows which is authoritative. One body, many thin pointers, keeps a single source of truth and makes adopting a new tool a one-line adapter, not a migration.

## Session start, session end

- **Start:** follow the read order. If the operator names a specific task, load the topics that task touches; you don't have to read everything every time, but you do have to read the top-of-log live state so you know where things stand.
- **End:** append one brief entry to the live-state log — what was done, where it stands, the next step. This is the handoff to the next session (which may be a compacted *you*). Keep it tight; link to context updates rather than restating them.

*Why this contract exists:* runtimes are disposable and context windows compact. The project's durable agent knowledge — not the agent's memory of the conversation — is what persists. If the boot contract is honored, any fresh session is as oriented as the last one. If it's skipped, the agent re-derives from scratch, re-asks answered questions, and re-litigates settled decisions. Reading is cheap; the re-derivation is not.

Whether a given session actually honors the boot is a **shared responsibility** between operator and agent — the steer can't mechanically enforce it, and shouldn't try (brittle forcing functions are worse than the problem). The design bet is that *indexed, load-on-relevance* reading is cheap enough to honor by default, and the operator steers when it drifts.
