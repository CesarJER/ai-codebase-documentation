# Style and Documentation Quality

## Reference hierarchy

Apply style guidance in this order:

1. Project/product-specific conventions.
2. Repository-wide documentation conventions.
3. General technical-writing guidance.
4. General editorial references.

Clarity and consistency for the actual audience outrank rigid application of a generic style rule.

## Default editorial style

When no stronger project convention exists:

- write directly and concisely,
- prefer active voice where natural,
- use one term consistently for one concept,
- define uncommon acronyms on first use,
- use descriptive headings,
- put critical information early,
- keep paragraphs focused,
- use ordered steps for procedures,
- start procedural steps with actions,
- distinguish code, commands, paths, config keys, and UI labels visually,
- state prerequisites before actions,
- state limitations where readers need them,
- avoid marketing language and unsupported superlatives,
- avoid filler summaries that merely repeat the preceding section.

Preserve the repository's language unless the user requests another language.

## Reader usability and accessibility

Keep heading levels logical, links descriptive, and procedures in execution order.
Explain necessary prerequisites before commands. Provide text explaining diagram
meaning and useful alternative text for images; avoid relying on color alone.
Use exact inspected UI labels and distinguish platforms or roles when actions differ.

Tables serve parallel lookup; long procedures and explanations usually work better
as steps or prose. Make status and limitations visible before readers rely on them.
Do not hide a critical qualification in a remote footnote or audit attachment.

Review a substantial guide as its intended reader: can they find the task, meet
prerequisites, distinguish placeholders, observe success, and recover from a known
failure? Report a walkthrough as simulated or static unless it was actually run.

## AI-specific failure modes

Actively check for:

- confident but ungrounded technical claims,
- invented commands/flags/parameters/UI labels,
- plausible stale documentation rewritten as if current,
- excessive repetition,
- generic prose that does not help the intended reader,
- over-documentation of obvious implementation details,
- inferred intent presented as historical fact,
- silently changing terminology,
- claiming checks/tests were run when they were not.

Require evidence for factual technical claims rather than "sounding right".

## Quality dimensions

Evaluate substantial documentation against:

### Accuracy

Does it describe the current system correctly?

### Completeness

Does it contain enough information for the intended reader/task without trying to document everything?

### Relevance

Does it avoid obsolete or unnecessary content?

### Findability

Can readers locate the information where they would reasonably expect it?

### Task success

Can the intended reader successfully complete the documented task?

### Maintainability

Is the documentation connected closely enough to its source of truth to resist drift?

### Consistency

Do terminology, naming, structure, and formatting align with the rest of the project?

### Safety

Could following the documentation create avoidable operational, security, privacy, or data-loss risk?

### Verifiability

Can important claims be traced to evidence?

## Review discipline

For substantial edits:

- prefer focused changes over unrelated rewrites,
- preserve useful surrounding content,
- distinguish factual correction from stylistic preference,
- re-read the full affected section after editing,
- verify that a clearer sentence did not accidentally broaden or narrow the technical claim.
