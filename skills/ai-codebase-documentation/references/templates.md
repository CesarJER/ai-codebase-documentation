# Adaptable Documentation Templates

Use only when no existing repository format fits. Replace illustrative placeholders with inspected facts, omit irrelevant fields, and preserve the repository language. These templates are examples, not a required schema or reason to create more files.

## Documentation finding

```markdown
### DOC-01 — Concrete reader-impacting problem

- Priority: P1; claim status: CONTRADICTED.
- Location: docs/configuration.md, "Connection settings".
- Claim: the document says connection retries are unlimited.
- Evidence: src/connection.py, connect(), at inspected revision REVISION;
  retry_limit is finite after config parsing. Relevant test/observation: RESULT.
- Conditions/limits: ENVIRONMENT; deployment configuration not inspected.
- Impact: readers may expect recovery after the retry limit is exhausted.
- Action: document the limit, override, and observable terminal failure.
```

The names and behavior above are illustrative. A real finding needs actual sources, not copied values. Omit hypothetical findings after inspection disproves them.

## Change-impact table

| Changed contract/source | Affected doc/reader task | Decision | Evidence/validation |
| --- | --- | --- | --- |
| Actual symbol/key/path | Existing canonical doc and dependent page | Update / no change / generated / historical / unresolved | Inspected revision and relevant check |

## Configuration reference

| Key | Type/values | Effective default | Scope | Requirement/interaction | Source |
| --- | --- | --- | --- | --- | --- |
| Actual key | Verified parser semantics | Source fallback and overrides | Build/runtime; server/client; environment | Required/optional, restart, precedence, sensitivity | Source path/symbol |

Avoid recording live secret values. Explain precedence and what happens for missing, empty, malformed, or conflicting values when these differ. Add an example only if it clarifies correct use.

## Architecture explanation

```markdown
# System or subsystem name

Audience and scope, supported revision/version when needed.

## Responsibilities and boundaries

Major runtime units, owners established by the project, external systems,
trust boundaries and local/shared/persisted state.

## Key flow

A diagram or short sequence from trigger through validation, state and consumers.
Label permissions, transport, failure/recovery and data ownership where material.

## Constraints and trade-offs

Established decisions with links to ADRs; analysis labelled as analysis.

## Evidence and limits

Source pointers; what is source-verified versus integration/live-confirmed.
```

A C4 container denotes a runtime/deployable boundary; it is not necessarily a Docker container. Use fewer views when they already answer the reader's question.

## ADR

```markdown
# ADR identifier: Decision title

Status: proposed / accepted / rejected / superseded, using existing conventions.
Context: problem, constraints, and real alternatives considered.
Decision: what was chosen and why, supported by the decision record.
Consequences: benefits, costs, risks, and follow-up needs.
Relationships: supersedes/is superseded by another ADR when applicable.
```

Do not fabricate alternatives considered or acceptance dates. A reconstructed current analysis is not an accepted historical ADR.

## Runbook or how-to

```markdown
# Observable task or recovery goal

Applicability: environment/version and intended operator.
Prerequisites: permissions, tools, state assumptions, inputs and backup if needed.
Pre-checks: how to determine whether this procedure applies.

## Procedure

Ordered actions with shell/language, working directory, placeholders, expected
results and stop conditions. Identify destructive steps before readers reach them.

## Verification

Observable end state and a way to distinguish partial success.
Evidence level and steps not yet exercised in the target environment.

## Failure and recovery

Known symptoms, safe diagnostic checks, confirmed resolutions, rollback limits,
and escalation/next investigation. Never promise rollback without evidence.
```

## Historical finding resolution

| Original finding/snapshot | Remediation/source | Re-check actually performed | Current status and limits |
| --- | --- | --- | --- |
| Existing ID and original revision | Commit/path or documented action | Source / isolated test / integration / none | Resolved within scope / partial / unverified |

A successful build alone does not revalidate every original finding.

## Small maintenance note

When governance needs an existing page footer or index entry, record the owner
**only if established**, canonical source, change trigger, applicable version,
and validation pointer. Do not add a separate registry or timestamps without use.

