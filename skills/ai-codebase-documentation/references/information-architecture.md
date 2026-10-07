# Documentation Information Architecture

Use when authoring a document family or reorganizing docs. Start with readers and their tasks, then adapt the existing structure.

## Docs as code and navigation

Keep maintainable sources versioned/reviewed near their code where practical, with useful automated checks and attributable history. This does not require Markdown, a new site, or a specific framework.

Reuse the repository entry point. Keep a README or docs index as a useful route to canonical documents; link between related tasks rather than copying long explanations. A monorepo may need package-level entry points with clear shared-versus-package ownership and supported versions.

Preserve useful inbound links and anchors during moves. For lifecycle, generated/versioned docs, localization, and retirement read [maintenance](maintenance-and-change-impact.md).

## Diátaxis as a content decision

| Reader need | Form | Prioritize |
| --- | --- | --- |
| Learn by doing | Tutorial | A reliable learning path with observable progress |
| Complete a known task | How-to | Prerequisites, actions, expected result and limits |
| Look up exact behavior | Reference | Predictable facts, syntax, types, defaults and errors |
| Understand a system/decision | Explanation | Boundaries, relationships, constraints and trade-offs |

Use the distinction where helpful; do not create four empty directories or split a short coherent page into needless fragments. Link conceptual explanations from procedures and reference from examples.

## README

Usually include purpose/status, intended reader, verified prerequisites, the quickest useful entry path, essential commands, and links to deeper docs. State where commands run and which configuration is required.

Avoid making README the entire knowledge base. Keep private deployment details out of the public quickstart. Do not imply a minimal development setup reproduces production or all optional capabilities.

## Architecture and diagrams

Describe stable responsibilities, runtime/deployable units, dependencies, data ownership, trust boundaries, and important success/failure flows. Distinguish local, synchronized, derived, and persisted state when the system has those categories.

Choose only diagrams that answer a reader question:

- Context: users and external systems.
- Container: major runtime/deployable boundaries, not necessarily Docker containers.
- Component: internal responsibilities when materially useful.
- Sequence/data flow: order, authority, message transport, persistence, or recovery.
- Code-level: exceptional complexity or existing generated views.

Use C4 if it fits; preserve established alternatives. Keep a consistent abstraction level, title/scope, relationship labels, boundaries, and a legend when needed. Maintain diagram source beside the guide or through existing generation tooling. Validate diagram semantics against code, not just syntax.

For distributed or real-time systems, show who owns state, which roles can act, how commands are accepted, what transports carry data, what happens on disconnect, and what is intentionally local. Do not invent delivery, timing, ordering, or recovery guarantees.

## ADRs and decision records

Use ADRs for architecturally significant decisions. Reuse established numbering/status/template conventions. Capture context, actual decision, consequences/trade-offs, and status; include real alternatives only when supported.

Preserve accepted history. A changed decision gets a new record that supersedes the old one, with links in both directions as appropriate. If the original rationale is unknown, provide present-day analysis labelled as such; do not manufacture an accepted ADR.

## Configuration

Reference fields may include key, type/format, effective default, requirement, accepted values, sensitivity, scope, precedence, interactions, restart/rebuild requirements, and source.

Verify the reader/parser and deployment overrides. Distinguish manifest ranges from resolved dependency versions, sample values from executable defaults, and build-time client configuration from server runtime configuration. Explain missing/empty/malformed values when their semantics differ.

## API and asynchronous contracts

Document reader-relevant operations/events, purpose, auth and permissions, input/output schema, errors, side effects, limits, version/deprecation, and examples. Add idempotency, order, retries, or concurrency only with evidence.

Prefer executable schemas/specifications as syntax sources while checking parser/handler/consumer behavior. A machine-readable spec is not proof of enforcement. Surface discrepancies rather than making one source appear authoritative for every purpose.

## Operations and troubleshooting

A runbook needs applicability, prerequisites/permissions, pre-checks, ordered actions, expected outcomes, stop conditions, verification, known failures, and recovery/rollback limits when relevant. Mark destructive steps before execution.

Troubleshooting starts with an observable symptom, a diagnostic check that separates plausible causes, a supported resolution, and verification or next investigation. Label hypotheses. Never attribute a generic network/media symptom to a specific service without evidence.

Use [templates](templates.md) as optional starting points. Keep operational guides useful to operators; put code detail where it assists diagnosis or modification.

