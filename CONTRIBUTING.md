# Contributing to Codebase Documentation AI Skill

Thank you for considering a contribution.

This project aims to make AI-assisted software documentation **evidence-based, auditable, maintainable, and operationally safe**. Contributions are welcome when they improve that goal without turning the Skill into a repository-specific prompt or an oversized collection of generic writing advice.

## Licensing model

The public project is intended to be distributed under **GPL-3.0-or-later**. The Project Owner may also offer the Project under separate commercial terms.

The GPL permits commercial redistribution when its conditions are followed. A commercial license is therefore not a fee for merely making money with GPL-covered material; it is an alternative license for organizations that need rights beyond the GPL, such as proprietary redistribution or other terms incompatible with GPL copyleft requirements.

All merged contributions must be covered by the project's [Contributor License Agreement](CLA.md). The CLA allows contributors to retain ownership of their work while granting the Project Owner the rights required to maintain the dual-licensing model.

## Before you contribute

Please:

1. Read `SKILL.md` and the relevant files in `references/`.
2. Search existing issues and pull requests for related work.
3. For substantial changes, open an issue or discussion before investing heavily in an implementation.
4. Confirm that You have the right to submit the material.
5. Complete the project's CLA acceptance process before the contribution is merged.

If Your contribution was created as part of Your employment or for a client, make sure You have authority to contribute it.

## What makes a good contribution

Useful contributions include:

- stronger evidence and source-of-truth rules;
- better documentation-drift detection;
- safer audit workflows;
- improvements to change-impact analysis;
- clearer rules for comments, docstrings, examples, APIs, configuration, runbooks, ADRs, or architecture documentation;
- validation strategies that improve correctness without imposing unnecessary tooling;
- well-supported additions to `references/sources.md`;
- fixes for ambiguity, contradictions, excessive repetition, or rules that produce poor behavior in real repositories;
- examples demonstrating recurring documentation failures and how the Skill should handle them.

## Design principles

Contributions should preserve the following principles.

### 1. Technical truth before polish

Do not add rules that encourage the agent to infer technical behavior merely because it appears conventional or likely.

Material claims should be grounded in the appropriate evidence: implementation, tests, schemas, configuration, infrastructure, repository history, accepted design records, or authoritative version-relevant upstream documentation.

### 2. Uncertainty must remain visible

Do not replace missing evidence with confident prose.

The audit vocabulary exists for a reason:

- `VERIFIED`
- `PARTIAL`
- `STALE`
- `CONTRADICTED`
- `UNVERIFIED`
- `MISSING`

A contribution should not weaken the distinction between verified facts and inference.

### 3. Project conventions come first

The Skill must inspect and respect repository-local instructions before imposing generic documentation rules.

Avoid rules that force Diátaxis, C4, ADRs, a specific linter, or a particular documentation platform on repositories where those choices are inappropriate.

### 4. Keep the Skill tool-agnostic

Optional tools may improve discovery or validation, but the Skill should degrade gracefully when they are unavailable.

Do not make a proprietary MCP server, editor, code indexer, or documentation platform mandatory unless the entire project's scope changes accordingly.

When mentioning an optional tool:

- describe the capability required;
- distinguish the tool from the methodology;
- provide a reasonable fallback when possible.

### 5. Prefer progressive loading

`SKILL.md` is the control plane, not the knowledge dump.

Keep core routing, evidence rules, safety constraints, and workflow decisions in `SKILL.md`. Put detailed checklists and specialized guidance in `references/`.

As a default:

- keep `SKILL.md` below roughly 500 lines;
- keep reference files directly reachable from `SKILL.md` rather than creating deep reference chains;
- add a table of contents to long reference files where it materially improves navigation.

These are maintainability defaults, not arbitrary hard limits.

### 6. Avoid duplicated truth

Do not repeat the same normative rule across many files unless the repetition materially improves reliability.

Prefer one canonical rule with targeted references from the relevant workflows.

### 7. Safety boundaries are intentional

Do not weaken safeguards that prevent documentation tasks from unexpectedly:

- deploying software;
- changing production or remote state;
- running destructive migrations;
- discarding unrelated working-tree changes;
- restarting services merely to inspect documentation;
- changing application semantics solely to make documentation true;
- exposing secrets or personal/confidential information.

If a proposed change intentionally alters these boundaries, explain the use case and risk in the pull request.

## External guidance and sources

When adding a rule derived from an external standard, style guide, methodology, or vendor document:

1. Prefer primary or authoritative sources.
2. Add the source to `references/sources.md` when it materially informs the Skill.
3. Paraphrase the principle rather than copying substantial copyrighted text.
4. Explain why the guidance is generalizable to repository documentation.
5. Avoid presenting a vendor preference as a universal engineering rule.

For third-party framework or library behavior, verify the relevant version rather than documenting the latest version by assumption.

## AI-assisted contributions

AI tools may be used to help create contributions, but the human contributor remains responsible for reviewing what is submitted.

Before submitting AI-assisted work:

- verify factual and technical claims;
- check that cited sources actually support the rule;
- remove invented APIs, tools, capabilities, or repository behavior;
- check for accidental copying from external sources;
- remove confidential or personal information;
- ensure the contribution is understandable without hidden conversation context.

Do not submit large AI-generated rewrites that have not been manually reviewed.

## File-specific guidance

### `SKILL.md`

Modify `SKILL.md` when the change affects:

- triggering/scope;
- evidence hierarchy;
- operating modes;
- repository safety;
- routing to reference material;
- completion requirements;
- behavior that should apply to nearly every documentation task.

Avoid adding long domain-specific checklists to `SKILL.md` when they can live in a reference file.

### `references/audit-checklist.md`

Use for systematic audit coverage, drift patterns, verification states, severity, and reporting expectations.

### `references/code-comments-and-examples.md`

Use for comments, docstrings, public API descriptions, code snippets, pseudocode, and executable documentation examples.

### `references/information-architecture.md`

Use for document types and structure, including README scope, Diátaxis, architecture documentation, C4, ADRs, configuration reference, runbooks, troubleshooting, and historical documentation.

### `references/style-and-quality.md`

Use for technical-writing quality, terminology, clarity, usability, and recurring editorial failure modes.

### `references/tooling-and-validation.md`

Use for documentation builds, linters, link checkers, schema validators, example verification, CI, Context7, and optional tooling guidance.

### `references/sources.md`

Keep external provenance concise and authoritative. Do not turn this file into a general bibliography.

## Pull request scope

Prefer focused pull requests.

A good PR should answer:

- What problem does this solve?
- What failure mode or real use case motivated it?
- Which files need to change?
- Does this duplicate an existing rule?
- Could the rule create unnecessary work for ordinary documentation tasks?
- Does it introduce a tool dependency?
- Does it change safety or licensing behavior?

Avoid unrelated editorial rewrites in the same PR as a behavioral change.

## Testing a Skill change

Because this repository primarily contains agent instructions, review must go beyond Markdown syntax.

For meaningful behavioral changes, test the instruction against representative scenarios when practical, such as:

1. a stale README that conflicts with code;
2. a configuration default that differs between docs and parser/schema;
3. a third-party API whose current upstream docs differ from the repository's pinned version;
4. a historical ADR that should not be rewritten as current documentation;
5. an unverified security or privacy claim;
6. a code example containing a nonexistent flag or parameter;
7. a small documentation fix where the Skill should avoid a repository-wide rewrite.

Report notable behavior changes in the PR description.

Automated checks may include, when present in the repository:

- Markdown linting;
- broken-link checks;
- spelling or terminology checks;
- Skill validation/packaging;
- tests for helper scripts.

Passing automated checks does not by itself demonstrate that an instruction is technically sound.

## Pull request checklist

Before requesting review, confirm that:

- [ ] I have read the relevant project instructions.
- [ ] My contribution is focused and has a clear rationale.
- [ ] I have checked for conflicting or duplicated rules.
- [ ] I have verified factual claims and external references.
- [ ] I have not added secrets, personal data, or confidential material.
- [ ] I have identified any third-party material and its license.
- [ ] I have reviewed AI-assisted content rather than submitting it blindly.
- [ ] I have preserved the distinction between evidence and inference.
- [ ] I have not introduced a mandatory external tool without strong justification.
- [ ] I have run applicable repository checks.
- [ ] I have accepted the Contributor License Agreement through the designated CLA process.

## Commit messages

Use concise, descriptive commit messages. Conventional Commits are welcome but not required unless the repository later adopts them as a formal rule.

Examples:

```text
fix(audit): distinguish stale from contradicted claims
```

```text
docs(sources): add upstream guidance for ADR maintenance
```

```text
refactor(skill): move API checklist into reference guidance
```

## Review and acceptance

Maintainers may request changes when a contribution:

- cannot be supported by evidence;
- introduces excessive prompt weight for little benefit;
- duplicates existing guidance;
- makes optional tooling effectively mandatory;
- weakens safety boundaries;
- creates licensing/provenance uncertainty;
- is too repository-specific for the core Skill;
- adds complexity without a demonstrated documentation failure mode.

Not every good documentation practice belongs in the Skill. The goal is a small set of high-value instructions that materially improve agent behavior.

## Contributor rights

Contributors retain ownership of their original Contributions. The CLA grants the Project Owner rights needed to distribute, sublicense, and relicense those Contributions, including under separate commercial terms.

If You are not comfortable granting those rights, please do not submit material intended for inclusion in the Project. Issues, bug reports, and general discussion remain welcome unless they contain material explicitly intended for inclusion as a Contribution.

## Questions

For contribution questions, open a GitHub issue or discussion unless the matter involves security, private information, licensing of confidential material, or another issue that should not be public. For those cases, use the private contact method listed by the Project.
