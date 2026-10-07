# Evidence and Discovery

Use for technical verification, complex flows, high-impact claims, or uncertain evidence. Keep the evidence record proportional to the work; do not create a separate ledger for every sentence.

## Establish the snapshot

Identify repository/worktree, package, branch, commit or release, relevant dirty files, and scope. A commit identifies tracked committed code, not additional working-tree edits or a running deployment. When a check is sensitive to local changes, note that it examined the working tree.

Do not assume deployed software, container images, browser bundles, or server configuration match local HEAD. State the actual evidence boundary: source inspection, isolated test, local integration, or live observation.

For a graph/index, check the target repository and available freshness/coverage metadata. If the tool cannot establish revision, treat freshness as unknown. Re-index when needed and permitted; otherwise confirm relevant definitions and edges against current files. Missing nodes/callers can reflect unsupported languages, dynamic dispatch, configuration, or generated code. Empty search results do not prove absence.

## Discovery strategy

Follow repository-required tools first. If the codebase-memory-mcp tool is available in your environment:
1. Use `search_graph` to locate the actual symbol/route, narrowing by package, path, or label.
2. Inspect truncation and pagination; narrow or page before claiming full coverage.
3. Use `trace_path` for callers, dependencies, or cross-service/data flows. Include tests explicitly when relevant.
4. Use `get_code_snippet` with the returned qualified name to inspect definitions.
5. Use `query_graph`, `search_code`, or `get_architecture` only when they answer a remaining question.

Treat graph edges and architecture clusters as discovery, not proof of runtime behavior. Verify guards, registration, dynamic calls, and consequential absence claims in current source.

If codebase-memory-mcp is not available, or graph tooling is unavailable or insufficient, use targeted text search and file reads. Non-code documents, manifests, CI, deployment config, literal error messages, and environment keys usually need direct inspection. Search the relevant package, not all generated/vendor/data directories by default.

## Match the source to the claim

| Claim | Inspect | Common trap |
| --- | --- | --- |
| Runtime/default behavior | Implementation, callers, configuration precedence, conditions, tests | Function existence is mistaken for active execution |
| Public contract | Schema/signature, parser/validator, handler, consumers, contract tests | Types/specs omit actual validation and failure behavior |
| Config or environment | Reader/parser, fallback, startup/build/runtime scope, deployment overrides | Example value or dependency default presented as local default |
| Build/deploy commands | Script, lifecycle hooks, invoked scripts, manifests and outputs | A build triggers data generation, optimization, remote calls, or deployment |
| Persistence/retention | Writes, stores, deletion/expiry jobs, cleanup, backup/caching paths | Intended TTL mistaken for guaranteed deletion everywhere |
| UI and permissions | Current route/state, capability gates, server guards, tests | UI hiding, local identity, or transport connection treated as authority |
| Distributed/media behavior | Sender, transport, receiver, lifecycle/reconnect, relevant integration evidence | Unit tests treated as network, browser, SFU, or device proof |
| Architectural rationale | Accepted ADR/design record or explicit historical evidence | Current implementation used to invent original intent |
| Third-party contract | Resolved version and authoritative matching docs | Latest API silently substituted for installed version |
| Historical finding | Original snapshot, finding, reproduction and later resolution | A remediation or successful build treated as a repeated audit |

A test's assertions show what it checks. Mocked tests may not exercise real guards, storage, external services, timing, or devices. Read setup and compensating paths before concluding.

## Trace important claims end to end

For the claim under review, follow the relevant chain:

- Input/origin → validation and authority → state transition → transmission/storage → consumer → recovery/deletion.
- Configuration source → parse/coercion → fallback/override → build or runtime application.
- Feature flag → packaging/startup → capability/permission gate → enabled/disabled behavior.
- Client command → server acceptance → downstream service result → local state publication → failure reconciliation.

Inspect callers and both success/failure paths where they change the claim. Separate state intent, acknowledgment, server acceptance, and observed external behavior.

For multi-client systems, identify roles and authority, local versus synchronized versus persisted state, transports/trust boundaries, revisions/order/idempotency, disconnect recovery, and what tests actually exercise. These dimensions apply to collaborative apps, real-time tools, media systems, and ordinary client/server products; do not introduce architecture merely to document them.

## Resolve conflicting evidence

Check revision, environment, scope, and executable path first. An accepted ADR records a decision; it cannot override contradictory implementation when describing current behavior. A schema may define an intended contract while a handler diverges: document the discrepancy and classify an implementation defect separately. Do not silently declare one source universally authoritative.

If rationale is unavailable, describe the current trade-off as analysis, not a historical decision. If intended behavior is clear but unimplemented, label it proposed or intended.

## Compact evidence record

For consequential findings record:

- Documentation path/section and precise claim.
- Claim status and affected revision/environment.
- Source path plus symbol/config key/schema; inspected line or commit permalink when useful.
- Evidence kind: source, test/assertion, isolated reproduction, integration, or live observation.
- Conditions, counterevidence, and limits.
- Impact and recommended documentation action.

Put bulky evidence in an audit/review artifact only when requested or warranted. Reader-facing guides should remain usable; link to the source or evidence at the point where it helps.

## Privacy and operational claims

Separate technical product facts, deployment-specific configuration, and operator/legal decisions. Product code does not establish organization-wide compliance, lawful basis, supplier practice, live infrastructure, or a retention policy actually adopted by an operator.

Use synthetic identifiers and placeholders. Avoid copying private environments, tokens, personal transcripts, hosts, accounts, or local absolute paths into public examples. Inspect only the necessary private fields and summarize without exposing values. Check tracked status and effective ignore rules for the precise destination when relevant; ignored files are not an access-control mechanism, and already-tracked files remain tracked.

For sensitive operations, inspect commands statically before deciding how to validate. An unverified recovery procedure must state its prerequisites and limits; do not execute it against live systems merely to validate prose.

