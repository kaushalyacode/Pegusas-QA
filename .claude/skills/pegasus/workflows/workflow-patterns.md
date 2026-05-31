# Workflow Patterns (Orchestration Reference)

Agent sequencing for each Pegasus skill. `→` = depends on previous; agents on the same line may run in parallel. Spawn via the Task tool with `subagent_type` = agent name. Full narrative: `PEGASUS_WORKFLOWS.md` at the repo root.

## BRD (`/pegasus-from-brd`)
qa-requirement-analyst + qa-domain-specialist → qa-field-traceability-specialist → qa-workflow-specialist → qa-test-designer → qa-ui-report-validator → qa-risk-assessor → **assemble**

## Jira (`/pegasus-from-jira`)
qa-requirement-analyst → qa-workflow-specialist → qa-test-designer → **assemble**

## Field Traceability (`/pegasus-field-traceability`)
qa-field-traceability-specialist → qa-ui-report-validator → qa-test-designer → **assemble**

## Multi-Screen / Workflow (`/pegasus-workflow-testing`)
qa-workflow-specialist → qa-field-traceability-specialist → qa-ui-report-validator → qa-test-designer → **assemble**

## UI ↔ Report (`/pegasus-ui-report-validation`)
qa-field-traceability-specialist *(if needed)* → qa-ui-report-validator → qa-test-designer → **assemble**

## Defect (`/pegasus-bug-report`)
qa-defect-analyst → **assemble**

## Release (`/pegasus-test-summary`)
qa-defect-analyst → qa-risk-assessor → qa-release-assessor → **assemble**

## Artifact flow (never skip upstream)
Requirement Analysis → Field Traceability → Workflow Analysis → Test Scenarios → Test Cases → Validation Matrix → Execution → Defects → Release Report
