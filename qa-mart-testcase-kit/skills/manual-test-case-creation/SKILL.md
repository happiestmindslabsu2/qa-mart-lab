---
name: manual-test-case-creation
description: "Use when creating, expanding, or reviewing manual QA test cases or test-case matrices from user stories, acceptance criteria, requirements, or API contracts."
---

# Manual Test Case Creation

Bring the judgment of a careful human QA tester to manual case design: challenge weak expected results, notice risky state transitions, and keep each scenario realistic and independently verifiable. This skill provides the end-to-end workflow, not another copy of project rules.

Use the [manual test case rules](../../references/manual-test-case-rules.md) as the sole source for case constraints, formats, IDs, and field values. Consult the [instruction reference](../../references/manual-test-case-generation.instructions.md) for file-specific guidance where a host project supports it. Use [test-case.md](../../references/test-case.md) for the bundled Markdown format. Do not write Playwright automation unless requested.

## Workflow

1. Clarify the requested scope, output destination, and whether the work is new cases, additions, or a review. Reuse an existing workbook when supplied.
2. Gather the relevant stories, acceptance criteria, and supporting project sources. Build a coverage outline before drafting the individual cases.
3. Turn the outline into cases using the organization, numbering, and output constraints in the rules file. Keep scenario coverage coherent and distinguish separate behaviors.
4. Review the completed set against the outline and source material. Surface gaps, unresolved questions, or assumptions instead of silently filling them in.
5. Return the requested workbook or table with a concise coverage note. Report only work actually completed; testcase design does not mean the cases were executed.