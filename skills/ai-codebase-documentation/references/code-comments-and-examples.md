# Code Comments, Docstrings, and Examples

Use native language conventions and existing project tooling/style. Preserve executable behavior and existing tool directives.

## Comments that earn their place

Explain non-obvious rationale, invariants, constraints, compatibility, side effects, security assumptions, performance ceilings, or workarounds and removal conditions. Avoid narrating syntax, repeating types, or stating unsupported historical intent.

Update a contradictory comment after tracing the actual path. Do not remove a useful constraint because the surrounding code looks straightforward. If the implementation violates the constraint, report the defect separately.

Comments may have executable/tooling effects: compiler/linter directives, coverage exclusions, code-generation markers, licenses, JSDoc/type directives, build tags, doctests, and structured annotation consumers. Python docstrings also change runtime __doc__ and can be read by tools. Inspect consumers before treating edits as prose-only; avoid changing these contracts incidentally.

## Public contracts

Document what callers need for safe use: purpose, parameters, returns, errors, side effects, preconditions, units, nullability, lifecycle, resource ownership, concurrency, and an example where material.

A strong type does not express all semantics: timestamps need units/clock, strings may encode formats, callbacks may have lifecycle constraints, and a promise may have rejection/cancellation behavior. Do not mechanically repeat already unambiguous signature information unless native tooling expects it.

Use actual signatures and parser/implementation behavior. Never invent APIs, defaults, exceptions, errors, or guarantees. Distinguish internal helpers from supported public contracts; do not imply every exported symbol is a stable external API.

## TODO and FIXME

Follow existing conventions. Keep notes actionable with enough context and issue linkage where expected. Do not invent issue IDs, turn suggestions into accepted requirements, or substitute TODOs for a required tracking workflow.

## Teaching examples

Use realistic reader tasks, the actual API, minimal unrelated code, clear synthetic data, and prerequisites. State shell/language, working directory, version assumptions, placeholders, and expected output where useful.

Mark pseudocode and partial snippets explicitly. Show omissions with appropriate comments or prose. Distinguish omitted error/cleanup/concurrency handling from recommended production behavior. Preserve security constraints even in short examples.

For secrets, show placeholders or verified environment lookup without real values. Do not add unsafe credential patterns merely to make a quickstart shorter.

## Verification

Inspect any effects before running examples. With existing safe tooling, verify imports/version, parse/type-check/compile/run, verify flags/config keys, and compare the actual expected outcome. Choose the smallest check that can expose a material failure.

A compiler proves syntax/types under that setup; an isolated mocked run does not validate an external service. State which checks ran and what could not be exercised. Never claim an example was tested by merely reading it.

## Maintainability

Prefer existing executable example sources, snippet extraction, doctests, or generation where already supported. Update the canonical source rather than its rendered copy. Do not build extraction infrastructure for one low-value snippet.

If code-adjacent documentation was the only authorized change, inspect the diff for altered code, imports, types, directives, or generated outputs before declaring it complete.

