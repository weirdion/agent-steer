# Self-Review

`verify before done` asks *does it work*. This asks a different question: *where is it wrong?* It's a
deliberate pass as a **reviewer, not the author** — the single highest-leverage habit before a commit
or a push. The author's frame is "here's why this is right"; the reviewer's frame is "assume this is
wrong somewhere, and go find where." An agent that just re-reads its own work in the author's frame
confirms its own assumptions. The perspective shift is the whole point.

Run it on non-trivial changes before committing, and again — for the staging and push questions —
before pushing.

## The ordered questions

Go through these against the actual diff, in order:

1. **What did I assume without checking?** Names, formats, an upstream's actual return shape, a
   library's real behavior. Assumptions are where confident-looking code is wrong.
2. **What did I write a comment (or a message) about that the code doesn't actually do?** A comment
   that describes an intention the code drifted from is a lie the next reader will trust.
3. **What's the blast radius if this is wrong?** Who else calls it, what breaks downstream, how far
   the damage reaches. This sets how hard to look at the rest.
4. **What does this log, store, or expose that it needn't?** Secrets into state or logs, data
   crossing a boundary it shouldn't, more surface than the task required.
5. **What does this assume that's true today but won't be later?** A constant that will drift, an
   ordering that holds only by luck, a format that will break its consumers on the next change.

**Verify assumptions by reading the source, not by reasoning about it.** When the review turns up "I
think the upstream returns X" — go read what it actually returns. Reasoning about behavior is how the
assumption survived into the code in the first place; the review's job is to break it by looking, not
to re-run the same reasoning.

Report what the pass finds **plainly, including your own errors.** A self-review that only confirms
the work is theater. The output that earns its cost is "I found three things wrong," not "looks good."

## Verify the inputs, not just the syntax

A review that reads the changed files but not what those files *reference* misses a whole class of
failure. **Verifying a configuration is not verifying that what it references exists where it will
run.** A config can be internally valid and still fail on first execution because an input it depends
on isn't there.

Check the inputs the change assumes: files actually committed (not just present locally, and not
excluded by ignore rules), variables set, credentials granted, settings enabled, the referenced
resource actually created. The syntax being right is the cheap half; the referenced world being right
is the half that fails in the real run.

*Calibration:* look hardest at code that has **never been exercised** — unexercised integration and
glue between systems is where defects cluster, while settled, exercised code is usually clean. "It's
never been run but it's probably fine" is the assumption this pass exists to kill.

## Staging and push have their own reviews

The code review can be thorough and the *staging* still wrong. Three checks that live outside the diff:

- **Review what you're staging, not only what you wrote.** Look at the actual staged set before
  committing; never stage everything blind. The thorough part is easy to get right while a stray file
  the repo's own rules forbid rides along unnoticed.
- **Ask what *pushing* will do.** A push isn't inert — a pushed CI config runs, and can publish an
  artifact or trigger a downstream pipeline the moment it lands on the default branch. State what will
  run *before* pushing, not after it's already running.
- **Check CI after pushing.** A pipeline that fails silently on every push, with nobody looking, is a
  standing failure dressed as background noise. Red CI is a finding, not scenery — confirm green, or
  treat the red as the outstanding item it is.

*Why this is its own discipline, not a checklist item:* the failure it prevents isn't sloppy code —
it's *confident* code. The bugs a reviewer-frame pass catches are precisely the ones the author frame
couldn't see, because the author already believes them correct. The cost is a few minutes; the thing
it prevents is a false "done" built on an unchecked assumption, shipped and pushed.
