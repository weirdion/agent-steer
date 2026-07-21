# Backlog

Deferred steer work. Each entry: what it is, why it's parked, and what would pull it forward. If it isn't here and isn't in flight, it doesn't exist.

---

## Two-tier spine split (terse rules always-on + rationale on-relevance)

**What:** Split each `spine/` file into a terse always-loaded rule list and a separate on-relevance rationale file (e.g. `spine/conduct.md` keeps one-line rules; the *why*-paragraphs move to a `spine/conduct-rationale.md` pulled only when an agent must apply a rule to an edge case or is deciding whether to revise it). Roughly halves the always-on spine cost without deleting the reasoning — it moves one hop away.

**Why deferred (2026-07-20):** optimizes a cost already judged worth paying (see `decisions.md` — accept-the-spine). Doing it now is a YAGNI violation against the steer's own principles. The rationale is load-bearing — it's what lets an agent apply a rule to an unforeseen case, and what separates this steer from a cargo-cult principle list — so if this is ever done, *tier* the rationale, don't cut it.

**Pull-forward trigger:** a *gated* spine-only boot (INDEX + `spine/` only, on-relevance layers correctly not read) still measures too heavy in real use. Measure first; don't rebuild what isn't heavy.
