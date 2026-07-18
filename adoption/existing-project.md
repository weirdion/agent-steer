# Adopting an Existing Project

Retrofitting a repo that already has code, history, and maybe an ad-hoc agent setup — in whatever state it's in. This is the harder case: the project already carries knowledge, some of it in people's heads, some scattered, some stale. The goal is to bring it into the practice *without* a big-bang rewrite and without losing what the project already knows.

## The principle

**Assess first, then adopt incrementally.** Don't drop a full structure onto the project on day one. Learn what's there, recognize which knowledge purposes it already satisfies and how, propose the arrangement, and — once the operator ratifies — capture the gaps and mark the divergences. An existing project has earned scars; the job is to *recognize and capture* them, not overwrite them with generic defaults. Structure is proposed, not imposed (README two-altitude principle) — you find the shape, the operator confirms it.

## Steps

1. **Assess the current state.** What exists? Is there an ad-hoc prompt, scattered docs, a README that carries architecture, comments that encode conventions, a `git log` that reveals decisions? Where does the project's knowledge actually live today, and which of the knowledge *purposes* (see [../ways-of-working/knowledge-layers.md](../ways-of-working/knowledge-layers.md)) does it already satisfy — even under different names? Read before restructuring.

2. **Propose the arrangement, then get a yes.** From what you found, form a concrete recommendation: keep one agent context or split by purpose (coupling decides — a tightly-coupled project stays unified even when large); where agent-facing docs should live; what to add vs. leave as-is; which tools need a thin entrypoint. Present it with reasoning and wait for the operator to ratify before creating or moving anything structural. See [../ways-of-working/boot-contract.md](../ways-of-working/boot-contract.md) for the criteria.

3. **Add the steer pointer.** Point the project's boot sequence at the steer's `INDEX.md`. This immediately gives the project the spine, the ways of working, and preferences as inherited defaults — even before its own knowledge is reorganized.

4. **Recognize existing homes; route knowledge to them.** For each purpose, find where the project already serves it and keep using that home; only create a new one where the purpose is genuinely unmet. A project may already fold behavior-shaping lessons into its decisions log, or carry a domain catalog or contract ledger that doesn't match a named purpose — recognize it, identify the purpose it serves, and route new knowledge there rather than inventing a parallel structure. Where the project's knowledge is truly scattered with no home, propose one. Recoverable decisions (from history or docs) get seeded into the decisions home with their *why*; known-but-unbuilt work into backlog; recent state to the top of live state.

5. **Separate the universal from the earned.** An existing ad-hoc prompt usually mixes both: generic engineering advice (now redundant with the steer) and hard-won project specifics. Delete what the steer already covers. Keep what's genuinely local — and mark it LOCAL or OVERRIDE with its reason (see [override-convention.md](override-convention.md)). The test: remove a rule and ask whether the steer already says it. If yes, drop it. If removing it loses something real, it's a keeper.

6. **Add only the gaps the project needs, skip the rest.** A needs-verification checklist only if the agent can't run the thing. A memory home only when there's a real behavior-shaping lesson and no existing home already holds it. Don't manufacture empty structure to match a template — the purposes are jobs to be done, not boxes to fill. Where a track is personal or creative and carries identifying content (handles, names, private specifics), note that it must **never** be a source for promotion to the public steer (see [../ways-of-working/memory-discipline.md](../ways-of-working/memory-discipline.md) on redaction).

7. **Capture scars as you go, not all at once.** You won't recover every decision and convention on adoption day, and trying to will produce guesses. Adopt the scaffold, then let the real specifics land as the project is worked — each correction, each rediscovered constraint, gets written into the right layer when it surfaces. Adoption is the start of capture, not a one-time archaeology project.

## What "done enough" looks like

The project points at the steer, its existing knowledge is routed into the right layers instead of scattered, its genuinely-local rules are marked with their *why*, and a fresh session can boot cleanly. It does **not** mean every historical decision is reconstructed — that accrues over time. A partially-adopted project that boots cleanly and captures new scars correctly is in the practice; completeness follows from use.

*Why incremental beats big-bang:* a full retrofit in one pass forces guessing at reasons for decisions whose context is gone, and produces confident-looking fabrication. Adopting the scaffold and capturing specifics as they surface keeps the record *true* — every scar in the layers traces to a real moment, not a reconstruction.
