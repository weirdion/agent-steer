# Decisions

Settled choices about the steer itself, with date and rationale. Append-only — a decision stands unless a later dated entry deliberately revisits it. Records *why this and not that*.

---

## 2026-07-20 — Accept the always-on spine cost; gate the rest; defer any spine restructure

**Decision:** Keep paying the ~3k-token always-on spine cost as-is. Do **not** trim or restructure the spine to save boot tokens. Instead, harden the INDEX so on-relevance layers are *not read at boot* — make the frugal path the default, not a choice the agent can skim past.

**Context / the finding:** Live testing surfaced that reading the steer on boot spent more context than expected, and the concern sharpened into a real question: is the boot cost worth accepting, or worth optimizing? Measurement settled it.

- Always-on layer (INDEX + `spine/`) ≈ 173 lines / ~2,255 words / ~3k tokens.
- The whole repo ≈ 618 lines / ~10k words / ~13k tokens if read entirely.
- What the live test felt was not the 3k spine — it was the agent over-reading toward the full ~13k, pulling `ways-of-working/`, `adoption/`, `exemplars.md` that the task didn't need.

**Why accept the spine:** the spine buys senior-engineer *behavior from turn one* — verify before done, no sycophancy, ask before changing the requirement, security-as-default. The failure modes it prevents (a false "done," a silently-swapped requirement, a re-litigated decision) each cost far more than 3k tokens. It's cheap insurance, and its value is highest exactly at boot. Optimizing it is optimizing the wrong line item.

**Why gate the rest, not shrink it:** on-relevance content has *zero* value at boot — its right boot cost is zero, achieved by not reading it, not by making it smaller. The INDEX already promised load-on-relevance; the agent broke the promise because the instruction read as skimmable prose. The fix is a hard boot directive, not a redesign. ~2 lines changed.

**Why defer the two-tier spine split:** splitting each spine file into terse always-on rules + on-relevance rationale was the tempting optimization. Rejected preemptively as a YAGNI violation against the steer's own principles: it optimizes a cost already judged worth paying. It stays a logged option (see `backlog.md`) — revisit **only if** a *gated* spine-only boot still measures heavy in real use. Don't rebuild what isn't heavy.

**Bonus:** the INDEX gate makes the agent-steer blog post's claim ("load the small always-on spine") honest before it ships.

**The framing that resolved it:** accept vs. optimize is not one decision — it's per-layer. Pay for behavior always (always needed); pay for on-relevance content never, until its hook fires. What the test measured wasn't the cost of the design — it was the cost of the design not being followed, which is a far cheaper problem than a redesign.
