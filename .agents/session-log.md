# Session log

Live state for the steer itself. Newest first. Read the top first; write the top last. When a later session proves an entry wrong, mark it superseded — don't delete it.

---

## 2026-09-17 — FurDocs practices promoted; public-doc redaction rule extended

Cross-project practices from another repo's sessions were promoted into the steer. Several had
independently recurred (a phased "demonstrable slice" build and an ADR↔decisions pointer showed up in
a second project too), which is the steer's own promotion signal — earned, not guessed.

- **New** [`ways-of-working/self-review.md`](../ways-of-working/self-review.md), indexed on-relevance:
  the reviewer-perspective pass (*where is it wrong*, not *does it work*), verify-assumptions-by-reading-source,
  verify-inputs-not-just-syntax, and the staging/push/CI checks outside the diff.
- **`workflow.md`:** added "one path e2e before adding layers" and the three-condition sub-agent gate;
  self-review cross-link in the Verify step.
- **`knowledge-layers.md`:** "one home per fact, everything else a pointer" + "live docs hold live work,
  not history."
- **`collaboration.md`:** defend a sound proposal through a challenge rather than fold; explain-as-you-build
  when the operator is learning the stack.
- **`memory-discipline.md`:** wrong memory is worse than none — fix/delete stale in the turn noticed; plus
  (earlier this session) extended the redaction rule so a *project's* committed public agent docs carry only
  operate/agreements/context, not operator identity. See `decisions.md` for what was deliberately **not**
  promoted (defect-clustering) and why.

**Branch state:** all of the above is on branch `steer-boot-gate-and-self-context` (3 commits ahead:
`d7d4a25` redaction, `e742092` self-review, `02b2635` sharpenings), pushed to both remotes,
**not merged**. Next step is an MR to land it — that's when the promotions go live for adopting projects.

## 2026-07-20 — Boot-cost finding resolved; INDEX gated; self-referential `.agents/` added

- **Resolved** the boot-cost concern from live testing. Measured the always-on layer at ~3k tokens; concluded the spine cost is worth accepting and the real waste was over-reading the on-relevance layers. Full rationale in `decisions.md`.
- **Changed** `INDEX.md`: replaced the soft "load spine always, pull the rest on relevance" prose with a hard boot directive — read only INDEX + `spine/` at boot; nothing else until a hook fires. This is the whole fix (option A). ~2 lines.
- **Added** this `.agents/` directory so the steer tracks its own context/decisions/backlog/live-state instead of leaving findings in device-local memory. Closes the "steer has no self-referential home" gap.
- **Deferred** the two-tier spine split to `backlog.md` (YAGNI until a gated boot still measures heavy).
- **Next:** the agent-steer blog post can ship — the INDEX change makes its "small always-on spine" claim honest. Remaining for the post is the operator's call (alt-text, flip `draft=false`, commit/push). The device-local `agent-steer-boot-cost.md` memory is now superseded by this dir and can be trimmed to a pointer.
