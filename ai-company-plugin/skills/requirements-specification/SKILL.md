---
name: requirements-specification
description: Create structured requirements for software projects using EARS notation. Use when gathering user needs, structuring requirements, and defining acceptance criteria for implementation.
allowed-tools: Read, Write, Edit, AskUserQuestion
---

# Requirements Specification Skill

## Purpose
This skill helps create structured requirements documents using EARS (Easy Approach to Requirements Syntax) notation. It guides the process of gathering user needs, presenting high-level requirements for approval, and then creating detailed acceptance criteria for AI agents to implement.

## EARS Format Guidelines

EARS provides five primary patterns for writing clear, testable requirements.

### 1. Event-Driven Requirements
- **Pattern**: When [event], the [system] shall [response/action]
- **Use Case**: Responses to specific events or triggers
- **Example**: When user clicks checkout button, the Checkout Service shall validate cart contents

### 2. State-Driven Requirements
- **Pattern**: While [precondition], the [system] shall [response/action]
- **Use Case**: Behavior dependent on system state or preconditions
- **Example**: While payment is processing, the Checkout Service shall display loading indicator

### 3. Unwanted Behavior Requirements
- **Pattern**: If [trigger], then the [system] shall [response/action]
- **Use Case**: System response to errors, failures, or undesired situations
- **Example**: If invalid credit card number is entered, then the website shall display error message

### 4. Optional Feature Requirements
- **Pattern**: Where [feature is included], the [system] shall [response/action]
- **Use Case**: Requirements for optional or conditional features
- **Example**: Where the car has a sunroof, the car shall have a sunroof control panel

### 5. Ubiquitous Requirements
- **Pattern**: The [system] shall [response/action]
- **Use Case**: Always-active requirements and fundamental system properties
- **Example**: The mobile phone shall have a mass of less than 100 grams

### Combined Patterns
- While [precondition], when [event], the [system] shall [response/action]
- When [event] and [additional condition], the [system] shall [response/action]

## Subject Selection Guidelines
- **Software Projects**: Use concrete system/service name (e.g., "Checkout Service", "User Auth Module")
- **Process/Workflow**: Use responsible team/role (e.g., "Support Team", "Review Process")
- **Non-Software**: Use appropriate subject (e.g., "Marketing Campaign", "Documentation")

## Quality Criteria
- Requirements must be testable, verifiable, and describe a single behavior
- Use objective language: "shall" for mandatory behavior, "should" for recommendations
- Avoid ambiguous terms like "user-friendly", "fast", "secure" without measurable criteria
- Follow EARS syntax: [condition], the [system] shall [response/action]
- Requirement headings must include a leading numeric ID (e.g., "Requirement 1", "1.", "2 Feature")

## Requirements Document Structure

Requirements are created in **two stages**:

### Stage 1: Requirements Summary (for human approval)
Created first and presented to stakeholders for approval.

**Contents:**
- **Introduction**: Brief overview of the project and its goals
- **Requirements**: Organized by functional areas, each containing:
  - **Objective**: As a [role], I want [capability], so that [benefit]

**Purpose**: Allow stakeholders to approve WHAT to build without implementation details.

**Output**: `.ai-company/requirements-summary.md`
**Template**: `templates/requirements-summary.md` (exclude Attribution section)

### Stage 2: Requirements Detail (for AI implementation)
Created **only after** summary is approved by human stakeholders.

**Contents:**
- Everything from summary, plus:
- **Acceptance Criteria**: EARS-formatted detailed specifications for each requirement
- **Non-Functional Requirements**: Performance, security, scalability with measurable criteria

**Purpose**: Provide testable specifications for AI agents to implement and verify.

**Output**: `.ai-company/requirements-detail.md`
**Template**: `templates/requirements-detail.md` (exclude Attribution section)

## Process Guidelines

### Phase 1: Create Requirements Summary

#### Step 1: Initial Hearing
1. Receive user's initial feature/project description
2. Understand high-level goals and context

#### Step 2: Clarifying Questions
1. Identify ambiguities and gaps in high-level requirements
2. Ask targeted questions using AskUserQuestion tool
3. Focus on functional scope, user roles, and key scenarios
4. Ask about usage assumptions for cost estimation:
   - Expected number of users (initial, growth phase, stable phase if applicable)
   - Usage patterns (frequency, session duration, data operations per session, time of day, seasonality, storage retention)
5. Avoid asking about implementation details (HOW)

#### Step 3: Summary Organization
1. Structure requirements into logical functional areas
2. Write Objectives for each requirement: As a [role], I want [capability], so that [benefit]
3. Focus on WHAT the system should do, not HOW
4. Number requirements sequentially (Requirement 1, 2, 3...)
5. **Language**: Use the same language as user conversation (e.g., Japanese if user spoke Japanese)
6. Use templates/requirements-summary.md as structure guide

#### Step 4: Summary Review
1. Present requirements summary to stakeholder
2. Explain major functional areas and objectives
3. Highlight any assumptions made
4. Ask stakeholder to review for completeness and accuracy

#### Step 5: Summary Approval
1. Wait for stakeholder approval
2. If changes needed: Incorporate feedback and return to Step 3
3. If approved: Proceed to Phase 2

### Phase 2: Create Requirements Detail (After Approval)

#### Step 6: Detail Expansion
1. Take approved summary as base
2. **Language**: Write in English for AI agent consumption
3. Record user's language in Introduction section (same language used in requirements-summary.md)
4. For each requirement, add detailed Acceptance Criteria using EARS notation:
   - Event-Driven: When [event], the [system] shall [response]
   - State-Driven: While [precondition], the [system] shall [response]
   - Unwanted Behavior: If [trigger], then the [system] shall [response]
   - Optional Feature: Where [feature included], the [system] shall [response]
   - Ubiquitous: The [system] shall [response]
5. Add Non-Functional Requirements with measurable criteria
6. Add Usage Assumptions section:
   - User counts by phase (initial/growth/stable if large-scale, or single value if small-scale)
   - Usage patterns (frequency, session duration, data operations per session, peak times, seasonality, storage retention)
7. Use templates/requirements-detail.md as structure guide

#### Step 7: Detail Finalization
1. Ensure all acceptance criteria are testable and verifiable
2. Validate EARS syntax compliance
3. Requirements detail document is now ready for AI agents to use in implementation

### Next Phase

After completing `.ai-company/requirements-detail.md`, refer to the **ai-company-workflow** skill to proceed with Phase 2: Design.

## Common Pitfalls to Avoid
- Including implementation details in requirements
- Using vague or subjective language
- Missing error handling scenarios
- Requirements that cannot be tested
- Mixing multiple behaviors in a single requirement

---

## Attribution

This skill incorporates content from cc-sdd (https://github.com/gotalab/cc-sdd)
Copyright (c) 2025 gotalab
Licensed under the MIT License
