# Decisions

Settled choices about the steer itself, with date and rationale. Append-only — a decision stands unless a later dated entry deliberately revisits it. Records *why this and not that*.

---

## 2026-09-17 — Which cross-project practices to promote, and what to leave out

**Decision:** Promote a set of practices surfaced from another project's sessions (offered as candidates
for the steer), each stripped to its generalizable rule with the originating project's specifics removed.
Self-review became its **own** on-relevance file rather than a section of `verification.md`; the rest
attached to existing files (workflow, knowledge-layers, collaboration, memory-discipline).

**Why these:** each was a practice that had already earned its cost in real work, and two of them had
independently recurred in a second project — the steer's stated bar for promotion (recurrence across
projects = genuine invariant, not a guess; see `ways-of-working/knowledge-layers.md`).

**Why self-review as its own file:** `verification.md` answers *does it work* (verify by running, the
can't-verify case). The self-review pass answers a different question — *where is it wrong* — and is a
distinct discipline (adversarial perspective shift + blast-radius checks outside the diff) substantial
enough that folding it in would blur verification's focus. Loaded on relevance, not always-on: it applies
before a commit/push, not every turn.

**What was deliberately NOT promoted:**
- **Defect-clustering heuristic** ("bugs cluster in protocol/glue code"). Kept as a one-line *calibration*
  inside self-review, but **not** elevated to a steer rule — it's an empirical observation from one
  codebase, not a durable invariant, and the steer stays principle-level. If wanted as reviewer
  calibration it belongs in device memory, not the public steer.
- **Memory-placement restructure.** The candidate largely duplicated existing `memory-discipline.md`
  content (device-local vs repo-tracked, the project-or-operator test). Added **one** new crisp line
  (wrong memory worse than none) rather than restructuring a layer split that already works.

**The framing:** promotion is subtractive, not additive — the value is in what earns a place at the right
altitude, and saying no to the rest is what keeps the steer from bloating into a project's changelog.

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
