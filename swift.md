# Swift Style Guide

**PRINCIPLES**

* Favor pure, stateless, unit-testable functions; push side effects to the edges.
* Single responsibility; small, composable types and functions.
* Prefer structs/protocols over classes unless reference semantics are required.
* Minimal public surface; use the narrowest access level. Public/open only when necessary.

**NAMING & API**

* Use full words for all identifiers (no abbreviations): e.g., `isPublic`, `renderer`, `lineCount`.
* Clear, intention-revealing names; avoid Hungarian notation and terse single letters.
* Descriptive enum cases and method labels; prefer clarity over brevity.

**ERRORS & OPTIONALES**

* Use `throws` for recoverable errors; avoid silent failure.
* No force unwraps/tries in production code; handle or propagate errors.

**STYLE & LAYOUT**

* One blank line between logical blocks.

**Extensions & Conformance**

* Protocol conformance should be declared in extensions, not inline with the main type declaration.
* Keep protocol-required members inside the corresponding extension when possible.

**PROPERTIES & INITIALIZATION**

* Use lazy closure properties (`lazy var`) for expensive or multi-step initialization, keeping setup close to the property itself.
* Initializers should remain self-contained and side-effect free beyond constructing values.

**DOCUMENTATION & COMMENTS**

* Public APIs: brief `///` doc comment (single paragraph).
* Comments only when intent isn’t obvious; avoid redundant narration.

**TESTS**

* **One behavior per test.** State the intent in a single `///` line above the test.
* **Assert what matters.** Verify observable behavior and essential fields only; avoid over-asserting formatting/incidental details.
* **String outputs.** Prefer template-style expectations for Swift/JSON/text. Keep templates short; treat whitespace flexibly via the helper; avoid regex in templates. If using placeholders, define neutral ones (e.g., “ANY”, “EMPTY”) in the helper—not in the style guide.
* **Tiny shared helpers.** Only small, reusable utilities (e.g., a template matcher); avoid bespoke per-test helpers.
* **Minimal fixtures.** Build inputs inline when readable; extract a tiny builder only if reused.
* **Stable ordering.** Sort collections before asserting; don’t rely on non-deterministic iteration/hash order.
* **Readable failures.** Assertions should emit concise, human-legible diffs that highlight what changed and why.
* **Avoid brittle snapshots.** Prefer precise, minimal expectations over large snapshot files.

**DEPENDENCIES & INJECTION**

* Depend on protocols; inject collaborators via initializers/params.
* Keep units mockable without heavy frameworks.

**MISC**

* Prefer explicitness over magic; avoid hidden globals/singletons.
