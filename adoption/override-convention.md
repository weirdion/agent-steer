# Override Convention

The steer defines the canonical way of working. A project's local agent directory states only what *diverges*. This file defines how that divergence is marked, so a reader can always tell an inherited default from a deliberate local choice.

## The rule

Where a project is **silent**, the steer governs. Where a project has a rule, that rule **wins locally** — but it must be marked, with its reason, so it reads as an earned scar and not as drift.

Two kinds of local content:

- **LOCAL** — true for this project alone, with no steer equivalent. A stack-specific convention, a gotcha from this codebase, a constraint of this project's environment. It doesn't contradict the steer; it adds something the steer can't know.
- **OVERRIDE** — this project deliberately does something *differently* from the steer. It contradicts a steer default on purpose.

Mark both, and give the *why* — especially for an OVERRIDE, because a contradiction without a reason is indistinguishable from a mistake.

```
LOCAL: <the project-specific rule> — <why it's needed here>
OVERRIDE: <what the steer says> → <what we do instead> — <why this project diverges>
```

## Why mark it at all

An unmarked local rule raises a question every reader has to resolve: *is this a deliberate choice, a copy of something that drifted, or a mistake?* Marking it answers the question in place. An OVERRIDE especially: without the marker and the reason, the next session (or the next person) can't tell whether the divergence is load-bearing or an accident to "clean up" — and cleaning up a load-bearing scar reintroduces the bug it was preventing.

This is the same instinct as *document the why*: the reason is the part that doesn't survive unless written down.

## The thinning effect

A mature project adopted into the practice starts with a thick local agent directory — because it predates the steer and states everything itself. Over time, as its universal parts are recognized as *steer* material, they move up (or are simply deleted, because the steer already says them), and what remains is the LOCAL and OVERRIDE content: the project's actual, earned specifics.

A healthy adopted project trends toward a *thin* local layer — the steer carries the commons, the project carries its scars. If a project's local files restate things the steer already says, that's redundancy to trim, not content to keep. The test when trimming: **remove a local rule and ask whether the steer already covers it.** If yes, delete it. If removing it loses something real and project-specific, it was LOCAL — keep it, and make sure it's marked.

## When a local rule turns out to be universal

Sometimes a rule written as LOCAL is actually about *how the operator works* or *how any project should work* — it just happened to be discovered here. That's a promotion candidate for the steer (see [../ways-of-working/memory-discipline.md](../ways-of-working/memory-discipline.md)). Raise it. Once promoted and made project-agnostic, delete the local copy — it's inherited now.
