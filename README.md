# agent-steer

Directional guidance for coding agents. **Read it as steering — don't clone or copy it into a project.**

This repository is how a project's agent learns *how work is done here* and *how the operator likes to collaborate*, then applies that in the project's own idiom. It is a reference an agent consults, the way a new engineer reads a team's working agreements before touching the code — not a package that gets installed.

## What this is (and isn't)

- **It is** a small, indexed set of durable guidance in three layers: universal engineering + conduct principles, ways of working, and collaboration preferences.
- **It is not** a template to copy, a set of files to symlink, or a per-project ruleset. Nothing here is duplicated into a project. A project *points at* this repo and reads it.
- **It is not** project-specific. Nothing here names a repo, a stack, a machine, a path, or a person. Project-specific rules are *earned by that project* and live in that project's own `.agents/` directory. See [Steer defines, project overrides](#steer-defines-project-overrides).

## The three layers

| Layer | Changes | Loaded | Directory |
|---|---|---|---|
| **Spine** | Rarely | Always | [`spine/`](spine/) — universal engineering principles + agent conduct |
| **Ways of working** | As the practice gains scars | On relevance | [`ways-of-working/`](ways-of-working/) — how a project is structured, boot contract, knowledge layers, workflow, verification, memory |
| **Preferences** | As the operator's taste is learned | On relevance | [`preferences/`](preferences/) — how the operator likes to collaborate |

Read [`INDEX.md`](INDEX.md) first. It is one line per topic with a *when-this-applies* hook, so an agent loads the spine always and pulls the deeper layers only when they're relevant — instead of ingesting the whole repo and forgetting half of it by mid-session.

## How a project adopts this

A project opts in by naming this repo in its own boot sequence. Adoption is explicit and visible — you can tell which repos are in the practice by whether they point here.

```
# in a project's .agents/prompt.md, at the top of "Read first":
0. STEER — read <path-to>/agent-steer/INDEX.md, load the spine,
   pull ways-of-working / preferences on relevance. Then read the
   local files below, which state only what diverges from the steer.
```

To bring a project in — new or existing, in any state — follow the procedure in [`adoption/`](adoption/):

- [`adoption/new-project.md`](adoption/new-project.md) — scaffolding a fresh repo into the practice.
- [`adoption/existing-project.md`](adoption/existing-project.md) — retrofitting a repo that already has code and history.
- [`adoption/override-convention.md`](adoption/override-convention.md) — how a project's local files mark where they diverge from the steer, and why.

### Steer defines, project overrides

The steer holds the canonical ways of working. A project's local `.agents/` states only what is **local** (true for this project alone) or an **override** (this project deliberately diverges from the steer). Where a project is silent, the steer governs. Where a project has earned a local rule, the local rule wins **and the divergence is marked** so a reader knows it's a deliberate scar, not drift.

The consequence: a new project inherits the whole practice by writing almost nothing, and a mature project's `prompt.md` gets *thinner* over time as its universal parts move into the steer and only its earned, project-specific rules remain.

## Design constraints (for anyone editing this repo)

1. **Public and project-agnostic.** Treat every file as world-readable. No repo names, no stacks, no machines, no paths, no personal detail. If a rule can't be stated without naming a project, it isn't a steer rule — it's a project rule.
2. **Indexed, not dumped.** New guidance gets a one-line `INDEX.md` entry with a *when-this-applies* hook. Guidance that can't earn a hook probably isn't load-bearing.
3. **Rules carry their *why*.** A rule without a reason can't be applied to an edge case and can't be revised deliberately. State the reason, briefly.
4. **No invented precision.** Qualitative guidance an agent can actually judge — not fabricated metrics (complexity thresholds, health indices, decay rates) that read authoritative but measure nothing.
5. **Scars are welcome.** This repo evolves. When a lesson proves *universal* (not project-specific), it belongs here, with the reasoning that earned it. `git log` should read as the evolution of how work is done.

## Reference exemplars

Real projects that realize this practice are the best illustration of the principles — but they are **illustrations, not templates**. See [`exemplars.md`](exemplars.md). Do not copy their project-specific rules; read them to see the invariants *realized*.
