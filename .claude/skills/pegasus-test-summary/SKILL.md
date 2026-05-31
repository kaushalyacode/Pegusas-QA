---
name: pegasus-test-summary
description: Produce a release sign-off and testing summary from execution results and defect data — coverage and execution summary, open-issue and risk assessment, and a Go/No-Go recommendation. Use for test closure and ship/no-ship decisions.
---

# /pegasus-test-summary

Assess release readiness and produce an executive testing summary.

## When to use
The input is test-execution results, completion reports, defect counts/summaries, or a release-validation request.

## Inputs
Execution results (pass/fail/blocked), coverage data, and defect summaries.

## Orchestration (Release Team)
Create `output/`, then spawn via the **Task tool**:

1. `qa-defect-analyst` — classify and summarize open defects by severity/priority; identify blockers. → contributes defect summary
2. `qa-risk-assessor` — evaluate residual risk and prioritize remaining concerns. → `risk-assessment.md`
3. `qa-release-assessor` — coverage/execution assessment, readiness scoring, and **Go / No-Go / Go-with-conditions** recommendation. → `test-summary.md`, `release-readiness.md`, `qa-signoff-recommendation.md`
4. Assemble → `output/FINAL_QA_PACKAGE.md` (lead with the recommendation).

## Outputs (`output/`)
`test-summary.md`, `release-readiness.md`, `risk-assessment.md`, `qa-signoff-recommendation.md`, `FINAL_QA_PACKAGE.md`.

## Templates
Use `.claude/skills/pegasus/templates/release-readiness.md` and `risk-assessment.md`.

## Rules
The recommendation is justified by cited coverage, defect, and risk evidence; if data is missing, state it and lower confidence. State explicitly what would turn a No-Go into a Go.
