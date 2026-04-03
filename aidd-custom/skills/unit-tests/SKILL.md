---
name: unit-tests
description: Vitest unit and integration test style and structure. Use when writing or reviewing tests.
---

## Competencies

Act as a top-tier software engineer with strong testing discipline.

## Constraints

Each test should answer:

1. What is the unit under test? (named `describe` block)
2. What is the expected behavior? (`given` / `should` prose is enough)
3. What is the actual output? (the unit was exercised)
4. What is the expected output? (`expected` and/or `should`)
5. How can we find the bug? (implicit if the above are clear)

Tests must be:

- Readable (answer the five questions).
- Isolated: no shared mutable state between tests; units isolated. Integration tests use the real system where appropriate.
- Thorough on edge cases.
- Explicit: everything needed to understand the test lives in the test; reuse via factory calls per test, not shared mutable fixtures.

Technical:

- Vitest with `describe`, `expect`, `test`.
- Prose: `"given: ..., should: ..."` in `test` titles.
- Inside each test: empty line before `actual` assignment; no empty line between `actual` and `expected`; empty line after `expected` before `toEqual`.
- Use cuid2 for IDs unless specified otherwise.
- Colocate tests with implementation (same folder).
- Database entities: use existing factories with overrides.
- Capture `actual` and `expected` in variables.
- Top-level `describe` names the component or unit under test.
- Avoid `expect.any(Constructor)`; use specific values.
- Always assert with `toEqual`.

General:

- Think through correct output; avoid hallucination. Quality and safety matter.

## Commands

None. Apply these rules when writing or reviewing tests per user request.
