---
name: ai-company-workflow
description: Orchestrate the autonomous development lifecycle phases. Use when managing project workflow and phase transitions.
allowed-tools: Read, Write, AskUserQuestion, Task
---

# AI Company Workflow Skill

## Workflow Phases

### Phase 1: Requirements Definition

**Objective**: Gather and structure requirements for stakeholder approval

**Process**:
1. Use requirements-specification skill

**Human Interaction**: Approval required before proceeding to Phase 2

### Phase 2: Gap Analysis

**Objective**: Analyze implementation gap between requirements and existing codebase

**Process**:
1. Use Task tool to invoke validate-gap agent

### Phase 3: Design & Review

**Objective**: Create validated technical design

**Process**:
1. Use Task tool to invoke architecture-designer agent
2. Use Task tool to invoke design-reviewer agent

### Phase 4: Budget Approval

**Objective**: Estimate implementation costs and obtain budget approval

**Process**:
1. Use Task tool to invoke cost-estimator agent
2. Present cost estimate to user for approval
3. If approved: Proceed to Phase 4
4. If not approved:
   - Use AskUserQuestion to understand budget constraints and adjustment priorities
   - Return to Phase 1 to revise requirements

**Human Interaction**: Cost estimate approval required before proceeding to Phase 5

### Phase 5: Task Planning

**Objective**: Break down design into manageable implementation tasks

**Process**:
1. Use Task tool to invoke task-planner agent

### Phase 6: Implementation

**Objective**: Execute implementation tasks using Test-Driven Development

**Process**:
1. Use Task tool to invoke implementation-engineer agent
2. Agent executes all pending tasks in tasks.md using TDD cycle
3. Tasks are marked complete as they finish

### Phase 7: Validation

**Objective**: Validate implementation quality and fix all issues

**Process**:
1. Use Task tool to invoke validate-implementation agent
2. Agent validates and fixes:
   - All tasks completed
   - Tests pass
   - Requirements traceability
   - Design alignment
   - No regressions

### Phase 8: Deliverable Approval

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

### Phase 9: Steering Generation

**Objective**: Generate project memory for future development

**Process**:
1. Use Task tool to invoke steering-generator agent
2. Agent analyzes approved codebase and generates:
   - .ai-company/steering/product.md: Core capabilities and value proposition
   - .ai-company/steering/structure.md: Directory patterns and naming conventions
   - .ai-company/steering/tech.md: Tech stack and development standards
