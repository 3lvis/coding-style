PRINCIPLES
- Favor pure, stateless, unit-testable functions; push side effects to the edges.
- Single responsibility; small, composable types and functions.
- Prefer structs/protocols over classes unless reference semantics are required.
- Minimal public surface; use the narrowest access level. Public/open only when necessary.

NAMING & API
- Use full words for all identifiers (no abbreviations): e.g., `isPublic`, `renderer`, `lineCount`.
- Clear, intention-revealing names; avoid Hungarian notation and terse single letters.
- Descriptive enum cases and method labels; prefer clarity over brevity.

ERRORS & OPTIONALES
- Use `throws` for recoverable errors; avoid silent failure.
- No force unwraps/tries in production code; handle or propagate errors.

STYLE & LAYOUT
- One blank line between logical blocks; trim trailing whitespace; normalize to LF line endings.
- No line length.

### Extensions & Conformance
- Protocol conformance should be declared in extensions, not inline with the main type declaration.
- Group extensions with `// MARK: - <ProtocolName>` for clarity and discoverability.
- Keep protocol-required members inside the corresponding extension when possible.

PROPERTIES & INITIALIZATION
- Use lazy closure properties (`lazy var`) for expensive or multi-step initialization, keeping setup close to the property itself.
- Initializers should remain self-contained and side-effect free beyond constructing values.

DOCUMENTATION & COMMENTS
- Public APIs: brief `///` doc comment (single paragraph).
- Comments only when intent isn’t obvious; avoid redundant narration.

TESTS (XCTest)
- One focused behavior per test with a short `///` one-liner explaining what it verifies.
- Descriptive test names: `test<Behavior><Condition><Outcome>()`.
- No single-use helpers; share only tiny multi-use utilities (e.g., a regex matcher).
- Minimize fixtures; build inputs inline for readability.
- Avoid duplicate coverage—consolidate overlapping tests.

DEPENDENCIES & INJECTION
- Depend on protocols; inject collaborators via initializers/params.
- Keep units mockable without heavy frameworks.

MISC
- Prefer explicitness over magic; avoid hidden globals/singletons.
- Keep formatting consistent with Swift conventions and SwiftFormat-like rules.
