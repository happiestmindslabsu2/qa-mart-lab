# Manual Test Case Generation Instructions

This file is bundled as a reference. It is not automatically applied by the plugin because workspace instructions are not first-class plugin components.

When working in a project that supports file-specific Copilot instructions, apply these guidelines to manual testcase documents:

- Follow `manual-test-case-rules.md` for testcase constraints, formats, and controlled values.
- Use `test-case.md` as the Markdown table format unless the user requests another format.
- Read the in-scope story and acceptance criteria before writing cases; consult the API contract for API-level behavior.
- Preserve traceability to story and acceptance-criteria IDs. Flag unclear requirements rather than guessing.
- Keep case artifacts separate from Playwright automation. Do not modify the application to make expected behavior match observed behavior.
- Use the `manual-test-case-creation` skill for the complete generation and review workflow.