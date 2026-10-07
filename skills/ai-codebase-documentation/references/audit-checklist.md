# Documentation Audit Checklist

Use for comprehensive or risk-sensitive audits. For a narrow review, inspect only the affected claims and their dependencies.

## Coverage and inventory

Identify the target repository/packages, inspected revision and dirty state, document families, reader tasks, implementation areas, available tooling, and explicit exclusions. Do not call an audit comprehensive when substantial areas were sampled or inaccessible.

Include relevant root/nested READMEs, docs navigation, architecture/ADRs, API/event/schema reference, config and feature flags, build/operations, troubleshooting, security/privacy/data flows, onboarding, comments/examples, diagrams/screenshots, generated sources, and historical records.

Record document lifecycle separately from claim correctness. Check canonical destinations, duplicates, orphaned useful pages, versioned/localized copies, and private/public boundaries. Use [maintenance guidance](maintenance-and-change-impact.md) for a large inventory.

## Map claims to evidence

Trace the current sources for entry points, routes/events, roles and authorization, configuration precedence, flags, persistence/retention, external integrations, error/recovery paths, build hooks, and important reader workflows.

Use [evidence and discovery](evidence-and-discovery.md) to establish source/index freshness and distinguish source inspection, mocked tests, isolated reproduction, integration, and live observations. Read compensating guards and callers before accepting a suspected mismatch.

For claims using "always", "never", "guaranteed", "automatic", "encrypted", "anonymous", or "fully synchronized", inspect exceptions and conditions. Do not infer absence from one failed search.

## Claim states

Use these states or existing repository equivalents:

| State | Meaning |
| --- | --- |
| VERIFIED | Current evidence supports the claim within stated conditions and evidence level |
| PARTIAL | Broadly true but important conditions/limitations are omitted |
| STALE | Describes an older version, name, path, architecture, or behavior |
| CONTRADICTED | Current evidence directly disagrees |
| UNVERIFIED | Available evidence cannot establish the claim |
| MISSING | Important implemented behavior lacks reader-needed documentation |

Do not upgrade UNVERIFIED by assumption. Historical documents should be judged against their declared snapshot; a fixed historical finding is not automatically incorrect. If history is unavailable, do not invent an obsolete version to justify STALE.

## Drift checks

Investigate relevant categories:

- Renamed/deleted symbols, paths, packages, UI labels, URLs, or ports.
- Nonexistent commands, obsolete flags, prerequisites, working directories, shell incompatibility, unexpected lifecycle hooks.
- Environment/config keys, effective defaults, override/empty/invalid semantics, build/runtime scope, restart requirements.
- Auth, permission, request/response/error, concurrency/idempotency, and side-effect changes.
- Persistence, retention, caching, encryption, logging, recovery, and data ownership.
- Features disabled by flags, unavailable services, or role/capability gates.
- Stale diagrams/screenshots or architecture boundaries.
- Generated output out of sync with its source.
- Broken internal links/anchors and unreachable navigation.
- Conflicting current guides, language variants, or supported-version instructions.
- Historical plans presented as implemented behavior; remediations presented as independently revalidated findings.

Recommend missing docs only when absence materially harms onboarding, use, integration, safe maintenance, operations, security/privacy, or architectural understanding. Do not document trivial syntax for completeness.

## Severity based on demonstrated impact

Use repository severity conventions first. Otherwise:

| Priority | Threshold |
| --- | --- |
| P0 — Critical | A concrete, credible documented action or guarantee can cause severe exposure, destructive loss, irreversible change, or major outage |
| P1 — High | A material contract/operational/security/configuration mistake is likely to cause failed integration, unsafe operation, or consequential false assumptions |
| P2 — Medium | Incorrect, incomplete, or hard-to-find information causes meaningful task failure, engineering friction, or maintenance risk |
| P3 — Low | Editorial, formatting, or low-impact navigation/terminology issue |

Explain the causal path, affected reader/environment, prerequisites, and mitigating controls. Topic alone does not establish severity: a typo in a security page is not inherently P1. Keep uncertainty visible; do not exaggerate a hypothetical consequence or dismiss an unverified sensitive claim as harmless.

## Findings and delivery

For each material finding provide ID, priority, document location, precise claim/status, source evidence and revision, conditions/limits, reader impact, and recommended action. Use inspected source paths/symbols; include line numbers only when verified. See [templates](templates.md).

Group duplicate symptoms under their common documentation cause when useful. Separate documentation errors, missing topics, implementation defects, editorial preferences, and runtime hypotheses. Report counterevidence and drop disproven findings.

Conclude with coverage and exclusions, checks actually performed and their results, and unresolved questions. Do not imply that static checks establish runtime correctness. A review-only request produces findings; an audit-and-fix request can proceed with authorized documentation corrections and then report residuals.

