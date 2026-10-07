# Maintenance and Change Impact

Use for synchronization after code changes, documentation organization, or ongoing governance. Extend existing conventions rather than creating a parallel documentation system.

## Inventory only what the task needs

Start from README/docs navigation, local instructions, links from affected modules, documentation configuration, and canonical sources. Inventory relevant files with:

| Document/source | Reader and task | Lifecycle/version | Canonical source | Change trigger | Owner if established |
| --- | --- | --- | --- | --- | --- |
| Existing path | Who needs it and why | Current, historical, generated, draft, superseded, archived, or unknown | Code/schema/generator/ADR/doc | Concrete kind of change | Existing team/module owner or unknown |

Use a table only when it helps maintain multiple documents. Do not invent owners or create a central registry for a tiny repository. A generated document can also be current or version-specific: record generation separately when that distinction matters.

Find duplicate claims, competing entry points, orphaned useful pages, contradictory language variants, and inaccessible private dependencies. A page without an incoming link may be consumed externally; check before retiring it.

## Diff-to-document mapping

Establish the requested comparison: commit parent, explicit base/head, branch merge base, PR diff, or working-tree diff. Do not silently compare against an arbitrary default branch. Include added, modified, renamed, deleted, and authorized untracked files. Without history, analyze the available files and disclose that change impact is limited.

Use the diff to locate changed contracts; inspect surrounding current code, callers, tests, and configuration to understand the final behavior. Search relevant docs for old and new terms, paths, flags, endpoints, symbols, and reader workflows. Follow inbound documentation links and diagrams as needed.

| Change | Likely documentation impact |
| --- | --- |
| Endpoint/type/event contract | API/schema reference, client examples, auth/errors, version/deprecation notes |
| Default/config/env/feature flag | Configuration reference, sample config, quickstart, deployment variations, build/runtime scope |
| Auth/permissions/privacy/retention | Trust/data-flow docs, role tables, operational/privacy guidance and guarantees |
| Persistence/migration | Data model, upgrade/backup/recovery, compatibility and irreversible steps |
| UI flow or observable behavior | How-to, onboarding, screenshots and troubleshooting |
| Sync/media/reconnect semantics | Runtime roles, local/shared state, timing/order, recovery diagrams and validation limits |
| Build/toolchain/dependency change | Prerequisites, commands, CI/deployment guide and versioned examples |
| Module/path rename or deletion | Architecture/navigation, source links, examples, generated symbol indexes |
| Architectural decision | Current explanation; new/superseding ADR if a real decision was made |
| Pure internal refactor | Usually source links/comments only, unless documented boundaries or reader workflows changed |

Mark each candidate as update needed, reviewed/no change, generated-source change, historical/no rewrite, or unresolved, with a reason. No-doc-change is valid when the reader contract truly stayed the same; do not require ritual edits.

## Lifecycle and freshness

- **Current:** operational guidance for a specified supported revision/version and audience.
- **Historical:** dated/versioned record of decisions, incidents, audits, or releases.
- **Draft/proposed:** unaccepted guidance or behavior, clearly labelled.
- **Superseded/archived:** retained material with a successor or reason it is no longer active.
- **Generated:** output with an identifiable source and regeneration mechanism.

Do not stamp every file with today's date. A verified revision records the snapshot inspected; a review date records activity, not proof of permanent accuracy. Add metadata only when it answers a real reader/maintenance need or existing tooling expects it. Do not add unsupported frontmatter to a renderer.

For historical findings, preserve the original snapshot and severity. A new resolution should map finding IDs to fixes, evidence, re-check status, and remaining limits. Keep "implemented", "test passed", "finding revalidated", and "production confirmed" distinct.

## Generated and versioned documentation

Find the source and generator before editing output. Record the real command and output location when useful. Review generator hooks, data access, output files, environment, and network behavior before running it.

Regenerate through existing tooling when safe and in scope; compare the resulting diff. If regeneration requires private data, missing tools, live infrastructure, or unauthorized writes, update the allowed source and report the ungenerated output. Do not claim synchronization.

Keep documentation aligned to the release/version it serves. Do not rewrite older supported-version docs with new syntax. Respect existing localization relationships and default-language ownership. Update authorized affected variants, or state which translations remain unsynchronized; do not invent translated technical terms.

## Consolidation, moves and retirement

1. Identify the authoritative destination and unique useful content.
2. Inspect incoming links, navigation, scripts, generators, external references when known, and history.
3. Merge useful material without broadening unsupported claims.
4. Update authorized inbound links and preserve a redirect, stub, or stable anchor where needed.
5. Mark the former page superseded/archive it using repository conventions when retention is useful.
6. Validate navigation and review deletion/move effects.

Do not delete accepted records to reduce duplication. If external consumers are unknown, disclose that limit and favor preserving the old route rather than assuming no consumers.

## Governance that pays for itself

Tie upkeep to actual triggers: contract/default changes, a supported release, generator changes, major incidents, or a demonstrated onboarding failure. Prefer module owners and existing review workflows. Define who reviews technical truth, who reviews usability, and which checks are genuinely required.

When governance is requested, suggest the smallest intervention that prevents the observed problem: a docs-impact note in the existing PR template, an internal-link check, extraction of an already repeated example, or an ownership pointer. Avoid mandatory ADRs for trivial changes, arbitrary coverage percentages, new site frameworks, or many validators without a demonstrated benefit.

Proposed automation is not installed automation. Do not change CI, install tools, publish a docs site, create schedules, or modify unrelated policy without the task authorizing it.

## Delivery

Report changed canonical documents and reconciled dependents, intentional historical/generated/version exclusions, actual checks, and unresolved gaps. Group by reader-facing outcome rather than narrating every search. For a large update, the compact impact table in [templates](templates.md) can make coverage reviewable.

