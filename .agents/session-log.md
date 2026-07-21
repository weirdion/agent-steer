# Session log

Live state for the steer itself. Newest first. Read the top first; write the top last. When a later session proves an entry wrong, mark it superseded — don't delete it.

---

## 2026-07-20 — Boot-cost finding resolved; INDEX gated; self-referential `.agents/` added

- **Resolved** the boot-cost concern from live testing. Measured the always-on layer at ~3k tokens; concluded the spine cost is worth accepting and the real waste was over-reading the on-relevance layers. Full rationale in `decisions.md`.
- **Changed** `INDEX.md`: replaced the soft "load spine always, pull the rest on relevance" prose with a hard boot directive — read only INDEX + `spine/` at boot; nothing else until a hook fires. This is the whole fix (option A). ~2 lines.
- **Added** this `.agents/` directory so the steer tracks its own context/decisions/backlog/live-state instead of leaving findings in device-local memory. Closes the "steer has no self-referential home" gap.
- **Deferred** the two-tier spine split to `backlog.md` (YAGNI until a gated boot still measures heavy).
- **Next:** the agent-steer blog post can ship — the INDEX change makes its "small always-on spine" claim honest. Remaining for the post is the operator's call (alt-text, flip `draft=false`, commit/push). The device-local `agent-steer-boot-cost.md` memory is now superseded by this dir and can be trimmed to a pointer.
