# Manual Test Case Writing Rules

Use these rules when designing, reviewing, or exporting manual QA test cases for QA Mart.

## Sources of Truth

- Use the story acceptance criteria as the source for expected behavior.
- Use `docs/api/openapi.yaml` to confirm documented API inputs, responses, and errors when relevant.
- Use `docs/team-conventions.md` for project test conventions and `references/test-case.md` for this plugin's Markdown table format.
- Inspect the app only to understand how to perform a step or observe a result. Do not treat implementation behavior as a requirement when it conflicts with the story.
- If criteria are missing, ambiguous, or conflicting, record the question and do not invent an expected result.

## Test Design

- Trace each case to a story and acceptance-criteria ID, such as `US-101 AC3`.
- Break criteria into independently verifiable behaviors. Keep one primary behavior and outcome per case.
- Include relevant positive and negative paths, equivalence classes, boundary values, and state transitions. Use exact values immediately below, at, and above a specified threshold when applicable.
- Make state-dependent setup explicit, such as first-order versus returning-customer status. Use only data supported by the story, API contract, or existing test data.
- Select `UI` or `API` based on the behavior being verified. Choose a technique that explains why the case is included, and prioritize by user impact and risk.
- Organize cases by `module`, then by `scenario`. Assign a unique `scenario_id` to each module/scenario pair and reuse it for every case in that scenario.
- Give each test case a unique sequential `id` in workbook order, using `TC-001`, `TC-002`, and so on. Do not restart numbering for another module or scenario. When extending a workbook, preserve existing IDs and continue after the highest existing ID.

## Case Writing

- For Markdown output, follow the columns in `references/test-case.md`: ID, Story / AC, Title, Technique, Layer (UI/API), Preconditions, Steps, Expected, and Priority.
- Write reproducible steps with explicit setup and inputs. Make expected results observable and specific, including exact values or messages where requirements define them.
- Keep actions and expected results separate. Avoid vague outcomes such as "works" or "is correct".
- Do not duplicate cases just to increase case count. Identify uncovered criteria and assumptions in a short coverage note.
- A designed test case is not evidence that a test was executed. Do not report pass/fail status without execution evidence.
- Write to the destination requested by the user. If no file destination is requested, return the cases in the response rather than creating a new location.

## Excel Workbook Output

When Excel output is requested, create one row per test case with these required columns:

`scenario_id`, `module`, `scenario`, `id`, `description`, `requirement_refs`, `ac_refs`, `scenario_type`, `preconditions`, `assumptions`, `test_data`, `steps`, `expected_result`, `priority`, `severity`, `devices`, `browsers`.

The module may instead be provided once at the top level when it applies to every test case. The optional columns are `actual_result`, `status`, and `comments`. When `status` is omitted, default it to `Not Executed`.

The fields `preconditions`, `assumptions`, `test_data`, `steps`, and `expected_result` may each be a string or a list. Format list entries as numbered items in the cell. The fields `requirement_refs`, `ac_refs`, `devices`, and `browsers` may each be a list or a comma-separated string.

Use only these values for controlled fields:

- `priority`: `P1`, `P2`, `P3`, or `P4`.
- `severity`: `S1`, `S2`, `S3`, or `S4`. Descriptive forms such as `S1 - Critical` are also accepted.
- `status`: `Not Executed`, `Pass`, `Fail`, or `Blocked`.
- `scenario_type`: `Positive`, `Negative`, `Boundary`, `Edge`, `Error Handling`, `Recovery`, `Integration`, `State Transition`, `Usability`, `Accessibility`, `Regression`, `Non-Deterministic`, `Security`, or `Compatibility` (cross-browser and responsive).

For each clarification tracked as an open question, use `type` = `Question` or `Assumption` and `status` = `Open` or `Answered`. Keep unanswered items visibly open; do not silently turn them into test expectations.