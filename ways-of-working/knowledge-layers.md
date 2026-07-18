# Knowledge Layers

A project's durable knowledge is not one undifferentiated pile. It separates by **permanence and purpose**, and putting a fact in the wrong layer is what makes agent knowledge rot. The single most important discipline here: **durable truth and live state are different things and live in different places.**

These are **purposes, not mandatory folders.** Each names a *job* a project's knowledge has to do; how a project satisfies that job — a dedicated file, a section of a larger doc, or an existing structure that already serves the purpose — is a derivation the agent proposes, not a layout the steer imposes. A project may satisfy a purpose without a folder that shares its name, and may not need every purpose at all.

## The purposes

| Purpose | Holds | Permanence | Typical home (not required) |
|---|---|---|---|
| **Context** | What the project is, why it exists, how it's built, its load-bearing conventions | Durable; changes when the project's shape changes | indexed topic files |
| **Decisions** | Choices made, with date and rationale | Append-only; a decision is settled unless deliberately revisited | a decisions log |
| **Backlog** | Scoped-but-not-built work, each with a reason deferred and a pull-forward trigger | Durable until pulled forward or dropped | a backlog file |
| **Live state** | What just happened, what's in flight, the next step | Volatile; the top is the current handoff | a session log, newest first |
| **Needs-verification** | Shipped/designed things awaiting hands-on confirmation the agent can't perform | Volatile; cleared as items are verified | a checklist — needed only where the agent can't run the thing |
| **Memory** | Behavior-shaping lessons and operator preferences *not documented elsewhere* | Durable; corrected when contradicted | a git-tracked memory dir — see [memory-discipline.md](memory-discipline.md) |

Two of these — decisions and backlog — are the ones agents most often skip, and skipping them is expensive: a settled decision gets re-debated, a parked idea gets re-scoped from cold. Read them before starting new work.

## Recognize existing homes; don't manufacture layers

When adopting a project, the agent's job is to **recognize which purposes the project already satisfies and how** — not to create a folder per purpose. A project may fold behavior-shaping lessons into its decisions log and never have a separate memory dir; it may keep deferred work inside its live-state doc; it may carry a *contract ledger*, a *domain known-issues catalog*, a *per-language steering file*, or some other knowledge type the list above doesn't name.

The steer deliberately does **not** enumerate every possible knowledge type — that list is infinite and project-specific. Instead, when the agent meets a knowledge type that doesn't map cleanly to a purpose above, it:

1. **Recognizes** it and identifies which purpose it's serving (often it's a domain-specific flavor of context, memory, or reference).
2. **Places** it — routes new knowledge of that kind to the existing home rather than inventing a parallel one.
3. **Recommends**, doesn't impose: if the type looks like it deserves formalizing (or the project would be cleaner without it), the agent proposes that to the operator and leaves the call to them.

Do not create an empty layer just because the steer names it, and do not force an existing knowledge type into a steer purpose it doesn't fit. If the same unnamed type recurs across several projects, *that's* the signal it may be a genuine invariant worth promoting into the steer — earned from evidence, not guessed (see [memory-discipline.md](memory-discipline.md) on promotion).

*Why:* the purposes are stable; the physical layout is not. An agent that creates six named folders to match the table produces empty ceremony in a project that needed three; an agent that forces a contract ledger to *be* the decisions log loses what made it useful. Recognize the job, find where it's done, keep it there.

## The update trigger — the rule that keeps layers clean

When something changes, route it by significance:

- **Significant** — affects future work: a new subsystem, a convention change, an architectural shift, a decision worth referencing later. → **Update the durable context** (and log it in live state).
- **Routine** — fits existing patterns: a bug fix, a small feature, a tweak, a debugging session. → **Log it in live state only.**

When in doubt: log it, and if a future session would benefit from knowing, update context too. Don't wait to be asked to update context — that's part of doing the work, not a separate chore.

*Why the split matters:* if routine work bloats the durable context, the context stops being a reliable map — every read wades through noise. If significant changes only land in the session log, they scroll away and the next session rediscovers them by grepping prose. The trigger keeps the durable layer trustworthy and the volatile layer current.

## Defer at the moment of deferral

When you deliberately punt on something — cut from scope, blocked, judged not worth it yet — it goes in the **backlog right then**, with its shape, why it's deferred, and what would pull it forward. Not "later." Not "it's in the commit message."

*Why:* a deferral that lives only in a commit body or a session-log paragraph is invisible to the next session. It forces future-you to reconstruct what's pending by mining prose. Backlog-at-the-moment means: if it isn't tracked and isn't in flight, it doesn't exist — and that's a property you can trust.

## Live state carries the handoff — and its own corrections

The top of the session log is the current state: active work, the working agreement, the next step. Read it first; write it last.

When a later session proves an earlier entry *wrong* (a fix that didn't hold, a diagnosis that was mistaken), don't silently delete the old entry. Mark it superseded and keep it, with a pointer to what's correct now.

*Why keep the wrong turns:* the record of what you ruled out, and why, is often worth more than the answer — especially for debugging and root-cause work, where the value is "here's why the other four hypotheses were wrong," not just "here's the cause." A log that only shows the winning path invites the next session to re-explore the dead ends.

## Document the *why*, everywhere

Across all layers, favor the reason over the restatement. Decisions record *why this and not that*. Context explains *why it's built this way*. Commit bodies explain *why*, not *what*. The "what" is in the diff and the code; the "why" is the thing that doesn't survive unless you write it down.
