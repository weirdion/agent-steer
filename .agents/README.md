# .agents/ — the steer's own context

The steer eats its own cooking. This directory is `agent-steer`'s **self-referential** knowledge: the durable context, the decisions, the deferred work, and the live state *about the steer itself* — the same knowledge layers the steer asks every adopting project to keep (see [`../ways-of-working/knowledge-layers.md`](../ways-of-working/knowledge-layers.md)).

It exists because a steer that documents a practice but doesn't track its *own* open questions is asking projects to do something it doesn't do. Findings about the steer (a rule that's too heavy, a claim that isn't quite true, an idea deferred) now have a home here instead of floating.

**This is a public repo. Everything here is world-readable.** It holds only steer-specific, project-agnostic content — no PII, no operator profile, no machine paths, no other project's names or stacks. Anything about *the operator* (how they work, their preferences, personal context) lives in device-local memory, not here; only generalizable slices ever graduate up into `preferences/`.

Following the steer's own "recognize existing homes, don't manufacture layers" rule, this dir keeps layers minimal rather than one file per named purpose:

| File | Purpose it serves |
|---|---|
| `decisions.md` | **Decisions** — settled choices about the steer, with date and rationale. Append-only. |
| `backlog.md` | **Backlog** — deferred steer work, each with why it's parked and what would pull it forward. |
| `session-log.md` | **Live state** — what just changed in the steer and why; newest first. |

Context (what the steer *is*) already lives in `README.md` + `INDEX.md` at the root — no separate context file needed here. That's the "recognize existing homes" rule applied to the steer itself.
