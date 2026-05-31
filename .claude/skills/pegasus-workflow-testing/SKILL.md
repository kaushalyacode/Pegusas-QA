---
name: pegasus-workflow-testing
description: Generate end-to-end workflow validation — multi-screen flows, state transitions, approval processes, exception and rollback paths, and cross-system journeys. Use when testing multi-step processes rather than individual screens.
---

# /pegasus-workflow-testing

Generate end-to-end workflow and multi-screen validation suites.

## When to use
The request involves multiple screens, multi-step processes, approvals, lifecycle/state changes, or cross-system journeys (optionally with mockups).

## Inputs
Workflow/process description, screens or mockups, and relevant requirements.

## Orchestration (Multi-Screen workflow — Test Design + Validation Teams)
Create `output/`, then spawn via the **Task tool**:

1. `qa-workflow-specialist` — discover workflows, model states & transitions, derive happy/negative/exception/rollback paths. → `workflow-analysis.md`, `state-transition-matrix.md`, `workflow-validation.md`
2. `qa-field-traceability-specialist` — trace fields across the screens in the flow. → `field-traceability-matrix.md`
3. `qa-ui-report-validator` — validate data shown across screens and any resulting reports. → `ui-report-validation.md`
4. `qa-test-designer` — end-to-end and cross-screen scenarios + cases. → `end-to-end-test-scenarios.md`, `test-cases.md`
5. Assemble → `output/FINAL_QA_PACKAGE.md`

## Outputs (`output/`)
`workflow-analysis.md`, `state-transition-matrix.md`, `workflow-validation.md`, `field-traceability-matrix.md`, `ui-report-validation.md`, `end-to-end-test-scenarios.md`, `test-cases.md`, `FINAL_QA_PACKAGE.md`.

## Templates
Use `.claude/skills/pegasus/templates/workflow-validation.md`, `test-scenario.md`, `test-case.md`.

## Rules
Cover every allowed and disallowed state transition; include exception and rollback paths, not just the happy path.
