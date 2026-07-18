# Workflow

How a non-trivial task moves from intent to shipped. The loop is small and always the same; the rigor scales with the stakes.

## The loop

**Assess → Plan → Implement → Verify → Document**

- **Assess** — understand the task and its context before touching code. Restate the open questions. Think about the trade-offs against the project's long-term goals, not just the immediate ask. For anything non-trivial, a behavior-driven checklist — what should be true when this is done — beats diving in.
- **Plan** — for non-trivial work, a few bullets: the approach, the seams, what you're deliberately not doing. Reflect it in live state if it spans sessions. A real fork in approach is a place to surface options and let the operator choose (see [../spine/conduct.md](../spine/conduct.md)).
- **Implement** — keep changes scoped. Small, reviewable units over big leaps. Match the surrounding code's idioms — read like the code that's already there.
- **Verify** — run the tests, run the thing, confirm it works. If you can't run it, say so and hand over concrete verification steps. See [verification.md](verification.md).
- **Document** — update the right knowledge layer (see [knowledge-layers.md](knowledge-layers.md)). Durable change → context; routine → live state. Deferrals → backlog, at the moment you defer.

The loop is a spiral, not a line: verify can send you back to implement; assess can surface a fork that changes the plan.

## Small steps, testable along the way

Don't attempt a large change all at once. Break it into steps each of which can be verified before the next. Each step should add value and be reversible. A big-bang refactor with no checkpoints is how work goes off the rails — and how an agent, mid-way, quietly substitutes an easier target.

*Why:* incremental steps keep the blast radius small and the feedback fast. When something breaks, you know which step did it. When you're interrupted, you're at a clean boundary, not mid-leap.

## Stay in scope

Do the task in front of you. Don't fold in an ambitious refactor, delete adjacent code, or "improve" things you weren't asked about because you're passing by. Opportunistic cleanup is welcome *when it's in the blast radius of the change and the operator would want it* — not as an unrequested expansion. If you find a real problem outside scope, note it (backlog, or raise it), don't silently fix it.

*Why:* scope creep turns a reviewable change into an unreviewable one, and an unrequested refactor is a decision the operator didn't get to make. The diff should match the intent.

## Commits

- One logical change per commit. Small commits over big ones. Commit at sensible boundaries — a focused unit of work — not per line, not all at the end.
- Message: short imperative title. Body only when the *why* isn't obvious from the title and diff, and then kept tight. The body explains *why*, not *what*.
- No changelog-style comments in code ("this now…", "removed the call to…") — the diff and history carry that.
- Match the repo's existing message style. Credit AI assistance with a co-author trailer where that's the repo's convention.
- Don't skip verification hooks. Don't amend or force-push what's already pushed. Commit your own focused work — don't sweep unrelated dirty files into it.

*Why one-change-per-commit:* history is read to understand how the project got here. A commit that does one thing is a legible step; a commit that does five is a wall the reader has to untangle.

## When you're blocked

If the real approach is blocked, stop and surface it — the obstacle, the options, a recommendation. Don't quietly ship the easier thing (see [../spine/conduct.md](../spine/conduct.md)). Don't burn the session re-trying the same failing thing; after a genuine attempt, bring it back.
