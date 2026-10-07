# Tooling and Validation

Use existing tooling. Select checks that validate the changed reader task, not every possible checker.

## Inspect execution before running checks

Read the actual command, lifecycle hooks, invoked scripts, working directory, environment inputs, outputs, and relevant tool configuration. Even "build", "test", "preview", "--help", and "--dry-run" can execute arbitrary repository code or external requests.

Check for data generation, asset optimization, file rewrites, private dataset access, service startup, credential use, deployment, migrations, and remote writes. A dry-run flag is safe only to the extent its implementation is verified. Do not extract and run arbitrary fenced blocks from documentation.

Choose a safe existing narrower check, isolated fixture/workspace, or static inspection if the normal command has side effects outside scope. Do not bypass necessary hooks merely to declare a build passed; identify the exact narrower check and its limit.

## Validation layers

| Layer | Examples | What it establishes | What it does not establish |
| --- | --- | --- | --- |
| Structure | Markdown/MDX/site build, frontmatter/API schema, diagram parsing | Accepted syntax and build structure | Technical truth |
| Editorial | Terminology, spelling, prose lint | Local consistency/style rules | Implementation accuracy |
| Links/navigation | Repository paths, relative links, renderer anchors, redirects | Checked destinations are resolvable | Usefulness or all external accessibility |
| Executable examples | Parse/type-check/compile, doctest, isolated example | The checked example works under those conditions | Production equivalence |
| Contract/source review | Parser/handler/schema/config comparison, generator diff | Scoped agreement with inspected implementation | Live environment correctness |
| Integration/runtime | Authorized local integration or targeted live observation | Observed behavior in the recorded environment | Universal timing/device/network guarantees |

For internal links, resolve from the containing file and account for configured site roots, case-sensitive CI, renderer-specific anchors, renamed headings, assets, and redirects. Do not assume a filesystem-relative path is a valid site route or that an external timeout is a permanent broken link.

For diagrams, check both syntax and the actual relationships/flows. For screenshots, confirm the supported UI/version when practical.

## Example and generator checks

Verify shell/language, working directory, inputs, versions, imports, placeholders, and expected output. Never present a partial fragment as a complete executable example.

Run generators only after inspecting data and output effects. If outputs cannot be regenerated, report the source change and unsynchronized artifacts explicitly. Use [comments and examples](code-comments-and-examples.md) for native conventions and directive hazards.

## Context7 and upstream documentation

If the Context7 tool is available and library/framework/SDK/API/CLI/cloud-specific syntax or behavior matters: 

1. Identify the actual resolved version from the relevant package/lockfile, tool output, vendored source, or deployed image when in scope. A dependency range is not the resolved version.
2. With Context7, resolve the library name and question first unless the user supplied an exact library ID. Select a relevant reputable result, using version-specific IDs when available.
3. Query the user's full question scoped to one concept; separate unrelated concepts.
4. If results are incomplete, mismatched, or lack the used version, consult official version-specific docs/release notes/source. Disclose remaining version uncertainty.
5. Compare upstream statements with local wrappers, patches, configuration, and callers before writing a project claim.

Do not send secrets, personal data, private hosts, or proprietary snippets in documentation search queries. No upstream fetch is needed for a pure prose correction or business-logic review unless an external contract actually matters.

If Context7 is unavailable, rely on general web search tools (if permitted) or prompt the user to provide the authoritative upstream documentation if it is required to verify a claim.

## Incremental automation

When requested, use existing tooling categories: Markdown/prose/link checks, schema validators, native compilers/test runners, docs builds, diagram parsers, or generated-reference comparisons. Named tools are options, not installation requirements.

Prevent demonstrated recurring failures first. A link check or compiling one important example can be more valuable than broad editorial gates. Review CI command effects, runtime, network dependence, and false-positive policy before adding a gate. Do not make external transient failures indistinguishable from broken internal references.

## Report exactly what happened

For relevant checks, record command/check, scope/environment, result, and limit. Distinguish passed, failed, unavailable, and not run. Diagnose failures against the baseline when possible without discarding changes. Do not blame pre-existing failures without evidence.

After checks, inspect diff/status to catch generated or unexpected writes and distinguish them from prior work. Re-check consequential changed claims. Do not broaden or repeat checks after a pass without a new change or unresolved concern.

