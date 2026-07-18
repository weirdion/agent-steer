# Engineering Principles

Universal. These hold regardless of language, stack, or project. Each carries its *why* so it can be applied to an edge case and revised deliberately. None of them is a metric — they are judgments an agent makes, not thresholds to compute.

The stance behind all of them: **work like a senior engineer who will maintain this code in a year.** Clean, typed, tested, secure by default. Security is not a feature you add; it is the baseline you never drop below.

## DRY — one authoritative representation

Every piece of knowledge — a rule, a constant, a shape — has a single home. Duplicated logic drifts: one copy gets fixed, the other becomes a latent bug.

*Why it's not absolute:* premature abstraction to avoid two similar lines couples things that only look alike. Extract when the duplication is *knowledge* (the same decision expressed twice), not when it's *coincidence* (two things that happen to read the same today). When unsure, wait for the third occurrence.

## KISS — the simplest thing that works

Prefer the solution a maintainer understands in one read. Complexity is a cost paid every time someone touches the code, not just when it's written.

*Why:* most defects hide in cleverness. Simple code fails obviously; clever code fails subtly.

## YAGNI — build for what's needed now

Implement the feature in front of you, not the one you imagine. Speculative generality — the config knob nobody sets, the interface with one implementation — is guesswork that has to be maintained whether or not the guess was right.

*Why:* the future requirement usually arrives in a shape you didn't predict, and the pre-built abstraction is now in the way. Design *for* extension (clean seams), don't *pre-build* the extension.

## Single responsibility

A function, class, or module does one thing and means one thing. No multi-purpose variables, no behavior that changes with hidden context.

*Why:* a unit with one reason to change is testable, nameable, and safe to modify. One with several is a knot.

## Clarity over cleverness

Name things for what they are. Prefer predictable patterns and idioms of the language. The reader should not have to hold the whole file in their head to understand a line.

*Why:* code is read far more than written, and the reader is often you, six months out, with the context gone. Optimize for the moment of *not remembering*.

## Types and structure

Type the code. Use the language's constructs — classes, enums, dataclasses, interfaces, records — to make illegal states unrepresentable and to encode intent in the signature, where it makes sense. Don't pass untyped bags across module boundaries.

*Why:* a type is a proof the compiler checks and a note to the next reader. It moves a class of bugs from runtime to authoring time.

## Security is the default, not a pass

Assume every input is hostile until validated at the trust boundary. Secrets never live in code or git — only in a secret store or a gitignored local file, with a committed `.example` template. No dynamic execution of user-controlled strings. Sanitize anything that reaches the filesystem, a shell, or a query.

*Why:* a security gap is cheap to prevent and expensive to remedy — a hardcoded secret today is an incident at scale, an unvalidated path today is a traversal tomorrow. This is the one principle with no "when it's not absolute" — the cost asymmetry is too steep.

## Document the *why*, inline, not the *what*

Comments and commit bodies explain the reason, the trade-off, the non-obvious constraint. The code already shows *what* it does; the diff already shows *what* changed.

*Why:* "what" rots the moment the code changes; "why" survives, because the reason a decision was made outlives the specific lines. A `# why this package / this order / this guard` note is worth more in six months than any restatement of the mechanics.

## Optimize when it's proven, not when it's suspected

Write clear code first. Reach for performance work when a measurement shows it's needed, on the part the measurement points to — not on the part that felt slow.

*Why:* most code is not on the hot path, and optimizing the cold path buys nothing while costing clarity. Measure, then cut.
