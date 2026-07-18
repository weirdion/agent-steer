# Adopting an Existing Project

Retrofitting a repo that already has code, history, and maybe an ad-hoc agent setup — in whatever state it's in. This is the harder case: the project already carries knowledge, some of it in people's heads, some scattered, some stale. The goal is to bring it into the practice *without* a big-bang rewrite and without losing what the project already knows.

## The principle

**Assess first, then adopt incrementally.** Don't drop a full `.agents/` structure onto the project on day one. Learn what's there, map it onto the layers, fill the gaps, and mark the divergences. An existing project has earned scars — the job is to *capture* them, not overwrite them with generic defaults.

## Steps

1. **Assess the current state.** What exists? Is there an ad-hoc prompt, scattered docs, a README that carries architecture, comments that encode conventions, a `git log` that reveals decisions? Where does the project's knowledge actually live today? Read before restructuring.

2. **Add the steer pointer.** Point the project's boot sequence at the steer's `INDEX.md`. This immediately gives the project the spine, the ways of working, and preferences as inherited defaults — even before its own layers are organized.

3. **Map existing knowledge onto the layers.** Take what the project already has and route it (see [../ways-of-working/knowledge-layers.md](../ways-of-working/knowledge-layers.md)):
   - Identity and purpose → context (vision).
   - Structure → context (architecture).
   - Choices already made, recoverable from history or docs → seed a decisions log with them and their *why*.
   - Known-but-unbuilt work → backlog.
   - Recent state → the top of a live-state log.
   Move knowledge into its right home; don't leave it scattered.

4. **Separate the universal from the earned.** An existing ad-hoc prompt usually mixes both: generic engineering advice (now redundant with the steer) and hard-won project specifics. Delete what the steer already covers. Keep what's genuinely local — and mark it LOCAL or OVERRIDE with its reason (see [override-convention.md](override-convention.md)). The test: remove a rule and ask whether the steer already says it. If yes, drop it. If removing it loses something real, it's a keeper.

5. **Fill the gaps the project needs, skip the ones it doesn't.** Add a needs-verification checklist only if the agent can't run the thing. Add a memory dir when there's a real behavior-shaping lesson to record. Don't manufacture empty structure to match some template — the layers are homes for knowledge that exists, not boxes to fill.

6. **Capture scars as you go, not all at once.** You won't recover every decision and convention on adoption day, and trying to will produce guesses. Adopt the scaffold, then let the real specifics land as the project is worked — each correction, each rediscovered constraint, gets written into the right layer when it surfaces. Adoption is the start of capture, not a one-time archaeology project.

## What "done enough" looks like

The project points at the steer, its existing knowledge is routed into the right layers instead of scattered, its genuinely-local rules are marked with their *why*, and a fresh session can boot cleanly. It does **not** mean every historical decision is reconstructed — that accrues over time. A partially-adopted project that boots cleanly and captures new scars correctly is in the practice; completeness follows from use.

*Why incremental beats big-bang:* a full retrofit in one pass forces guessing at reasons for decisions whose context is gone, and produces confident-looking fabrication. Adopting the scaffold and capturing specifics as they surface keeps the record *true* — every scar in the layers traces to a real moment, not a reconstruction.
