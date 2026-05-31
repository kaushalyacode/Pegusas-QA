# Pegasus Workflow Orchestration

## Purpose

This document defines collaboration between skills and agents.

All agent references use the canonical subagent identifiers defined in PEGASUS_SUBAGENTS.md (the `qa-*` names). The orchestration layer is the `/pegasus` skill, referenced here as "Pegasus."

---

# BRD Workflow

Input:

BRD

Process:

Step 1

qa-requirement-analyst

↓

Step 2

qa-domain-specialist

↓

Step 3

qa-field-traceability-specialist

↓

Step 4

qa-workflow-specialist

↓

Step 5

qa-test-designer

↓

Step 6

qa-ui-report-validator

↓

Step 7

qa-risk-assessor

↓

Final Assembly

Pegasus

Outputs:

* Requirement Analysis
* Gap Analysis
* Domain Analysis
* Workflow Analysis
* Traceability Matrix
* Test Scenarios
* Test Cases
* UI/Report Validation
* Risk Assessment

---

# Jira Workflow

Input:

Jira Story

Process:

qa-requirement-analyst

↓

qa-workflow-specialist

↓

qa-test-designer

↓

Pegasus

Outputs:

* Story Analysis
* Test Cases
* Workflow Coverage

---

# Field Traceability Workflow

Input:

Fields, Data Mappings, Integrations, Reports

Process:

qa-field-traceability-specialist

↓

qa-ui-report-validator

↓

qa-test-designer

↓

Pegasus

Outputs:

* Field Traceability Matrix
* Data Lineage Report
* Field Validation Test Cases

---

# Multi-Screen Workflow

Input:

Requirements

Screens

Mockups

Process:

qa-workflow-specialist

↓

qa-field-traceability-specialist

↓

qa-ui-report-validator

↓

qa-test-designer

Outputs:

* Workflow Validation Matrix
* Traceability Matrix
* Cross-Screen Test Cases

---

# Defect Workflow

Input:

Bug Description

Process:

qa-defect-analyst

↓

Pegasus

Outputs:

* Structured Defect Report

---

# Release Workflow

Input:

Execution Results

Process:

qa-defect-analyst

↓

qa-risk-assessor

↓

qa-release-assessor

↓

Pegasus

Outputs:

* Coverage Report
* Risk Assessment
* Release Recommendation

---

# Enterprise Workflow Pattern

Pegasus should automatically detect:

State Transitions

↓

Approval Processes

↓

Publishing or Deployment Processes

↓

Reporting and Data Flow Processes

Generate:

* Workflow Tests
* Validation Tests
* Regression Tests

without requiring explicit instructions.

---

# Artifact Flow

Requirement Analysis

↓

Field Traceability

↓

Workflow Analysis

↓

Test Scenarios

↓

Test Cases

↓

Validation Matrix

↓

Execution

↓

Defects

↓

Release Report

No downstream artifact should skip upstream analysis.
