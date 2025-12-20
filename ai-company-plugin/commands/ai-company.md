# AI Company - Autonomous Development Workflow

Execute the complete autonomous development lifecycle from requirements to deployment.

## Workflow Overview

This command orchestrates development through phases with minimal human intervention:
1. Requirements Definition → 2. Gap Analysis → 3. Design & Review → 4. Budget Approval → 5. Task Planning → 6. Implementation → 7. Validation → 8. Deliverable Approval → 9. Steering Generation

**Human Interaction Points**: Requirements approval (Phase 1), Cost approval (Phase 4), Deliverable approval (Phase 8)

---

## Phase 1: Requirements Definition

**Objective**: Gather and structure requirements for stakeholder approval

### EARS Format Guidelines

EARS (Easy Approach to Requirements Syntax) provides five primary patterns for writing clear, testable requirements:

1. **Event-Driven**: When [event], the [system] shall [response/action]
2. **State-Driven**: While [precondition], the [system] shall [response/action]
3. **Unwanted Behavior**: If [trigger], then the [system] shall [response/action]
4. **Optional Feature**: Where [feature is included], the [system] shall [response/action]
5. **Ubiquitous**: The [system] shall [response/action]

**Quality Criteria**:
- Requirements must be testable, verifiable, and describe a single behavior
- Use objective language: "shall" for mandatory behavior
- Avoid ambiguous terms without measurable criteria
- Requirement headings must include a leading numeric ID

### Step 1: Initial Hearing
1. Receive user's initial feature/project description
2. Understand high-level goals and context

### Step 2: Clarifying Questions
1. Identify ambiguities and gaps in high-level requirements
2. Ask targeted questions using AskUserQuestion tool
3. Focus on functional scope, user roles, and key scenarios
4. Ask about usage assumptions for cost estimation:
   - Expected number of users (initial, growth phase, stable phase if applicable)
   - Usage patterns (frequency, session duration, data operations per session, time of day, seasonality, storage retention)
5. Avoid asking about implementation details (HOW)

### Step 3: Create Requirements Summary
1. Structure requirements into logical functional areas
2. Write Objectives for each requirement: As a [role], I want [capability], so that [benefit]
3. Focus on WHAT the system should do, not HOW
4. Number requirements sequentially (Requirement 1, 2, 3...)
5. **Language**: Use the same language as user conversation (e.g., Japanese if user spoke Japanese)
6. Use `templates/requirements-summary.md` as structure guide (exclude Attribution section)
7. Output: `.ai-company/requirements-summary.md`

### Step 4: Summary Review & Approval
1. Present requirements summary to stakeholder
2. Explain major functional areas and objectives
3. Highlight any assumptions made
4. Ask stakeholder to review for completeness and accuracy
5. **Wait for stakeholder approval**
6. If changes needed: Incorporate feedback and return to Step 3
7. If approved: Proceed to Step 5

### Step 5: Create Requirements Detail (After Approval)
1. Take approved summary as base
2. **Language**: Write in English for AI agent consumption
3. Record user's language in Introduction section (same language used in requirements-summary.md)
4. For each requirement, add detailed Acceptance Criteria using EARS notation
5. Add Non-Functional Requirements with measurable criteria
6. Add Usage Assumptions section:
   - User counts by phase (initial/growth/stable if large-scale, or single value if small-scale)
   - Usage patterns (frequency, session duration, data operations per session, peak times, seasonality, storage retention)
7. Use `templates/requirements-detail.md` as structure guide (exclude Attribution section)
8. Ensure all acceptance criteria are testable and verifiable
9. Validate EARS syntax compliance
10. Output: `.ai-company/requirements-detail.md`

**Common Pitfalls to Avoid**:
- Including implementation details in requirements
- Using vague or subjective language
- Missing error handling scenarios
- Requirements that cannot be tested
- Mixing multiple behaviors in a single requirement

---

## Phase 2: Gap Analysis

**Objective**: Analyze implementation gap between requirements and existing codebase

**Process**:
1. Use Task tool to invoke validate-gap agent

---

## Phase 3: Design & Review

**Objective**: Create validated technical design

**Process**:
1. Use Task tool to invoke architecture-designer agent
2. Use Task tool to invoke design-reviewer agent

---

## Phase 4: Budget Approval

**Objective**: Estimate implementation costs and obtain budget approval

**Process**:
1. Use Task tool to invoke cost-estimator agent
2. Present cost estimate to user for approval
3. If approved: Proceed to Phase 5
4. If not approved:
   - Use AskUserQuestion to understand budget constraints and adjustment priorities
   - Return to Phase 1 to revise requirements

**Human Interaction**: Cost estimate approval required before proceeding to Phase 5

---

## Phase 5: Task Planning

**Objective**: Break down design into manageable implementation tasks

**Process**:
1. Use Task tool to invoke task-planner agent

---

## Phase 6: Implementation

**Objective**: Execute implementation tasks using Test-Driven Development

**Process**:
1. Use Task tool to invoke implementation-engineer agent
2. Agent executes all pending tasks in tasks.md using TDD cycle
3. Tasks are marked complete as they finish

---

## Phase 7: Validation

**Objective**: Validate implementation quality and fix all issues

**Process**:
1. Use Task tool to invoke validate-implementation agent
2. Agent validates and fixes:
   - All tasks completed
   - Tests pass
   - Requirements traceability
   - Design alignment
   - No regressions

---

## Phase 8: Deliverable Approval

**Objective**: Obtain stakeholder approval for deployment

**Process**:
1. Use Task tool to invoke deliverable-approver agent
2. Agent generates:
   - deliverable-summary.md: Implemented features, test results, cost verification
   - deployment-guide.md: Deployment steps and verification procedures
3. Present deliverables to user for approval
4. User deploys and verifies the system using deployment-guide.md

**Human Interaction**: Approval required
- User reviews deliverable-summary.md
- User deploys system following deployment-guide.md
- User verifies deployment and provides approval

---

## Phase 9: Steering Generation

**Objective**: Generate project memory for future development

**Process**:
1. Use Task tool to invoke steering-generator agent
2. Agent analyzes approved codebase and generates:
   - .ai-company/steering/product.md: Core capabilities and value proposition
   - .ai-company/steering/structure.md: Directory patterns and naming conventions
   - .ai-company/steering/tech.md: Tech stack and development standards

---

## Attribution

This command incorporates content from cc-sdd (https://github.com/gotalab/cc-sdd)
Copyright (c) 2025 gotalab
Licensed under the MIT License
