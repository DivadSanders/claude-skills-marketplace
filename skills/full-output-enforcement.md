---
name: full-output-enforcement
description: "When the user needs complete, unabridged output — full files, all components, every function, no skipping. Use when the user says 'write the full file,' 'don't skip anything,' 'complete implementation,' 'no placeholders,' 'I need the whole thing,' or when the task clearly requires exhaustive output (full codebases, complete documents, all sections)."
category: productivity
tags: [output-quality, completeness, code, no-truncation, production, full-file]
version: 2.0.0
author: DivadSanders
---

# Full Output Enforcement

> A partial output is a broken output. This skill eliminates truncation, placeholders, and incomplete implementations entirely.

## What This Does

Overrides Claude's default behavior of shortening responses when they get long. Enforces complete code generation — every file, every function, every section, delivered in full with no shortcuts.

## When to Use

- Any task requiring a complete file (not a sketch)
- Writing 5 components? You need all 5.
- Multi-section document? You need every section.
- You keep getting "// implement here" or "...rest of code"

## Example Prompts

- "Write the full implementation of my auth service — no placeholders"
- "Generate all 8 components. I don't want stubs."
- "Write the complete landing page copy — every section, nothing skipped"

---

## Baseline Rule

Treat every task as production-critical. A partial output is a broken output. Do not optimize for brevity — optimize for completeness. If the user asks for a full file, deliver the full file. If the user asks for 5 components, deliver 5 components. No exceptions.

---

## Banned Output Patterns

The following are hard failures. Never produce them:

**In code:**
- `// ...`
- `// rest of code`
- `// implement here`
- `// TODO`
- `/* ... */`
- `// similar to above`
- `// continue pattern`
- `// add more as needed`
- bare `...` standing in for omitted code

**In prose:**
- "Let me know if you want me to continue"
- "I can provide more details if needed"
- "for brevity"
- "the rest follows the same pattern"
- "similarly for the remaining"
- "and so on" (when replacing actual content)
- "I'll leave that as an exercise"

**Structural shortcuts:**
- Outputting a skeleton when the request was for a full implementation
- Showing the first and last section while skipping the middle
- Replacing repeated logic with one example and a description
- Describing what code should do instead of writing it

---

## Execution Process

1. **Scope** — Read the full request. Count how many distinct deliverables are expected (files, functions, sections, answers). Lock that number.
2. **Build** — Generate every deliverable completely. No partial drafts, no "you can extend this later."
3. **Cross-check** — Before outputting, compare deliverable count against the scope count. If anything is missing, add it before responding.

---

## Handling Long Outputs

When a response approaches the token limit:

- Do not compress remaining sections to squeeze them in
- Do not skip ahead to a conclusion
- Write at full quality up to a clean breakpoint (end of a function, end of a file, end of a section)

End with:

```
[PAUSED — X of Y complete. Send "continue" to resume from: <next section name>]
```

On "continue": pick up exactly where you stopped. No recap, no repetition, no preamble.

---

## Pre-Output Check

Before finalizing any response, verify:

- [ ] No banned patterns appear anywhere in the output
- [ ] Every item the user requested is present and complete
- [ ] Code blocks contain actual runnable code — not descriptions of what code would do
- [ ] Nothing was shortened to save space
- [ ] Deliverable count matches the requested scope
