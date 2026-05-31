# Pegasus Skill Implementation Guide

## Purpose

This document defines how the Pegasus Framework is implemented using Claude Code Skills and Subagents.

Pegasus follows a modular, agent-driven architecture designed for complex enterprise application testing across multiple domains and industries.

Each skill and subagent has a clearly defined responsibility.

The main Pegasus skill acts as the orchestration layer, coordinating specialized analysis, validation, and test-generation capabilities.

---

# Skill Architecture

```text
.claude/

agents/                          # specialist subagents, spawned via the Task tool
├── qa-requirement-analyst.md
├── qa-field-traceability-specialist.md
├── qa-workflow-specialist.md
├── qa-ui-report-validator.md
├── qa-test-designer.md
├── qa-defect-analyst.md
├── qa-release-assessor.md
├── qa-domain-specialist.md
└── qa-risk-assessor.md

skills/

pegasus/                         # orchestrator skill + shared assets
├── SKILL.md
├── templates/                   # test-scenario, test-case, regression-suite,
│                                #   field-/requirement-traceability-matrix,
│                                #   workflow-validation, ui-report-validation,
│                                #   bug-report, risk-assessment, release-readiness
├── knowledge/                   # enterprise-testing-heuristics.md
└── workflows/                   # workflow-patterns.md

pegasus-from-brd/
├── SKILL.md

pegasus-from-jira/
├── SKILL.md

pegasus-field-traceability/
├── SKILL.md

pegasus-workflow-testing/
├── SKILL.md

pegasus-ui-report-validation/
├── SKILL.md

pegasus-bug-report/
├── SKILL.md

pegasus-test-summary/
├── SKILL.md
```

---

# Core Orchestration Skill

## /pegasus

### Purpose

Acts as the central orchestration engine for all Pegasus workflows.

### Responsibilities

* Detect input type
* Classify testing objective
* Determine execution workflow
* Invoke appropriate skills
* Coordinate subagents
* Aggregate outputs
* Generate final QA package

### Supported Input Types

#### Requirements

* BRD
* Functional Specification
* Technical Specification
* User Story
* Epic
* Feature Documentation

#### Development Artifacts

* Jira Ticket
* Change Request
* Enhancement Request

#### Validation Inputs

* Screenshots
* Mockups
* UI Designs
* Reports
* Analytics Outputs
* Export Files

#### Testing Inputs

* Test Results
* Defect Information
* Execution Logs

### Output

Comprehensive QA Package containing:

* Requirement Analysis
* Workflow Analysis
* Field Traceability Matrix
* Test Scenarios
* Test Cases
* Validation Reports
* Defect Reports
* Release Readiness Assessment

---

# /pegasus-from-brd

## Trigger

Requirement documents including:

* BRDs
* Functional Specifications
* Business Requirements
* Change Requests

## Responsibilities

### Requirement Analysis

* Parse requirements
* Identify business rules
* Identify workflows
* Identify actors
* Identify dependencies
* Identify assumptions

### Data Analysis

* Identify entities
* Identify fields
* Identify transformations
* Identify validations

### Test Design

* Generate test scenarios
* Generate positive test cases
* Generate negative test cases
* Generate boundary test cases
* Generate integration test cases

### Enterprise Analysis

* Effective dating requirements
* Lifecycle and state management workflows
* Access and eligibility validations
* Configuration impacts
* Compliance and governance considerations
* Cross-system integration dependencies
* Data quality and reconciliation requirements

## Output Artifacts

* requirement-analysis.md
* business-rules.md
* workflow-analysis.md
* gap-analysis.md
* risk-assessment.md
* test-scenarios.md
* test-cases.md

---

# /pegasus-from-jira

## Trigger

Jira stories, defects, enhancements, and change requests.

## Responsibilities

### Story Analysis

* Parse acceptance criteria
* Identify impacted functionality
* Identify dependencies
* Identify workflow impacts

### Test Design

* Generate story-level scenarios
* Generate acceptance test cases
* Generate regression recommendations

### Traceability

* Map requirements to test coverage
* Identify coverage gaps

## Output Artifacts

* jira-analysis.md
* acceptance-test-scenarios.md
* acceptance-test-cases.md
* regression-impact-analysis.md

---

# /pegasus-field-traceability

## Trigger

Requirements containing fields, data mappings, integrations, reports, or workflow transitions.

## Responsibilities

### Field Identification

* Identify source fields
* Identify destination fields
* Identify calculated fields
* Identify derived values

### Traceability Analysis

* Track field movement
* Track transformations
* Track validations
* Track dependencies

### Validation Design

* Generate field validation scenarios
* Generate transformation validation scenarios
* Generate integration validation scenarios

## Output

* field-traceability-matrix.md
* field-validation-report.md
* transformation-analysis.md

---

# /pegasus-workflow-testing

## Trigger

Requirements involving:

* Multiple screens
* Multi-step processes
* Workflow transitions
* State changes
* Approval processes

## Responsibilities

### Workflow Analysis

* Identify workflows
* Identify actors
* Identify entry conditions
* Identify exit conditions

### State Validation

* Generate state transition tests
* Generate workflow progression tests
* Generate exception path tests
* Generate rollback scenarios

### End-to-End Testing

* Generate complete workflow scenarios
* Validate cross-system interactions
* Validate workflow dependencies

## Output

* workflow-analysis.md
* workflow-validation.md
* state-transition-matrix.md
* end-to-end-test-scenarios.md

---

# /pegasus-ui-report-validation

## Trigger

Reports, dashboards, exports, analytics reports, and UI-to-report validation requests.

## Responsibilities

### UI Validation

* Validate displayed values
* Validate calculations
* Validate formatting
* Validate filtering behavior

### Report Validation

* Validate report outputs
* Validate aggregations
* Validate sorting and grouping
* Validate export functionality

### Cross-Validation

* Compare UI values to report values
* Validate field consistency
* Validate transformation accuracy
* Validate reconciliation logic

## Output

* ui-validation-report.md
* report-validation-report.md
* ui-report-validation.md
* reconciliation-analysis.md

---

# /pegasus-bug-report

## Trigger

Issue descriptions, screenshots, logs, execution failures, and defect investigations.

## Responsibilities

### Defect Analysis

* Analyze issue details
* Identify impacted functionality
* Determine severity
* Determine priority

### Defect Documentation

Generate structured defects including:

* Summary
* Description
* Preconditions
* Steps to Reproduce
* Expected Result
* Actual Result
* Impact Assessment
* Severity
* Priority

## Output

* defect-report.md
* root-cause-analysis.md

---

# /pegasus-test-summary

## Trigger

Execution results, test completion reports, release validation activities, and defect summaries.

## Responsibilities

### Execution Analysis

* Analyze execution results
* Calculate coverage metrics
* Assess defect trends
* Evaluate risk exposure

### Release Assessment

* Determine release readiness
* Identify open risks
* Identify blocking issues
* Provide recommendations

### Reporting

Generate executive-level summaries and QA assessments.

## Output

* test-summary.md
* release-readiness.md
* risk-assessment.md
* qa-signoff-recommendation.md

---

# Shared Templates

All Pegasus outputs must use standardized templates to ensure consistency, traceability, and auditability.

## Required Templates

### Test Design

* Test Scenario Template
* Test Case Template
* Regression Test Template

### Traceability

* Field Traceability Matrix
* Requirement Traceability Matrix
* Workflow Traceability Matrix

### Validation

* UI Validation Report
* Report Validation Report
* Workflow Validation Report

### Defect Management

* Defect Report Template
* Root Cause Analysis Template

### Release Reporting

* Test Execution Summary
* Risk Assessment Report
* Release Readiness Report
* QA Sign-Off Report

---

# Skill Design Principles

All Pegasus skills must adhere to the following principles:

### Single Responsibility

Each skill performs one specialized function.

### Reusability

Skills can be invoked independently or as part of larger workflows.

### Traceability

All outputs must maintain linkage between requirements, workflows, fields, and test coverage.

### Domain Awareness

Skills should incorporate relevant business processes, operational workflows, regulatory requirements, governance controls, data management practices, and industry-specific considerations whenever applicable.

### Standardization

All generated artifacts must follow approved Pegasus templates and naming conventions.

### Orchestration First

The main Pegasus skill remains responsible for workflow selection, subagent coordination, and final output assembly.
