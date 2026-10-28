# QA Mart Copilot Instructions

This repository is a Playwright practice lab for the QA Mart app. Treat `app/` as the system under test: do not change it to make a test pass. Keep test changes in `tests/` and Page Objects in `pages/`.

## Playwright Conventions

- Specs live in `tests/<area>/<feature>.spec.ts`; lab work goes in `tests/lab/`. Add the story and acceptance-criteria ID (for example, `US-101 AC3`) to each test title or its `describe` title.
- Import `test` and `expect` from `tests/fixtures.ts` when a test needs the `api` or `signedInPage` fixture. Otherwise use the appropriate Playwright import, following nearby tests.
- Read credentials and product data from `tests/test-data.ts`; do not hard-code them in specs. Use `baseURL` and relative paths, not `http://localhost:3000`.
- Prefer locators in this order: `getByRole`, `getByLabel`, `getByText` for static copy, `getByTestId`, then CSS only as a last resort. Never use XPath, positional selectors such as `nth-child` or `.nth()`, or generated class names. The v2 redesign changes ordering and styling, while accessible names remain stable.
- Rely on Playwright auto-waiting and web-first assertions. Do not use `waitForTimeout` or read a value before asserting when the locator can be asserted directly.
- Keep assertions in specs, not Page Objects. Page Objects contain page-level locators and actions; use one class per `pages/<Name>Page.ts` file and do not default-export it.
- Keep each test focused on one behavior. Use `test.step` to make multi-step flows readable. Test both v1 and v2 where applicable.
- When a test exposes an app defect, keep the assertion and report the mismatch with `docs/templates/bug-report.md`. Do not weaken the test or alter the app.
- For manual test-case work, use the scoped workflow in `.github/instructions/manual-test-case-generation.instructions.md`.

## Patterns

Good: accessible locators, shared data, and assertions that wait for the UI.

```ts
import { test, expect } from '@playwright/test';
import { users } from '../test-data';

await page.getByLabel('Email').fill(users.locked.email);
await page.getByRole('button', { name: 'Sign in' }).click();
await expect(page.getByRole('alert')).toHaveText('This account is locked. Contact support.');
```

Avoid: hard-coded credentials, brittle selectors, fixed waits, and immediate reads.

```ts
await page.fill('#email', 'locked@qamart.test');
await page.waitForTimeout(1000);
const message = await page.textContent('.error');
expect(message).toBe('This account is locked. Contact support.');
```

## Before Handoff

Run the relevant checks for the change. For test changes, run `npm run typecheck`, `npm run lint:specs`, and `npm test`; run `npm run test:v2` when UI behavior is involved.