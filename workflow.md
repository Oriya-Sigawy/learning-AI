# CLAUDE_PROJECT_WORKFLOW.md

## Purpose

This document defines the development workflow for creating Python projects using Claude Code, Spec-Kit, and Git.

## Development Methodology

This workflow is based on Specification-Driven Development (SDD).

The primary source of truth is:

1. requirements.md
2. spec.md
3. plan.md

Code is an implementation of these documents and must remain aligned with them.

---

# PHASE 1 - PROJECT SETUP

## Step 1 - Initialize Repository And Connection To Speckit.

## Step 2 - Create claude.md

Create a `claude.md` file in the project root.

### Define Claude's Role

Claude acts as:

> Senior Python Software Engineer responsible for planning, implementation, testing, architecture, security, documentation and maintainability.

### Global Rules

Claude must:

* Follow requirements exactly.
* Follow the implementation plan.
* Never add features that were not explicitly requested.
* Never start coding before planning is approved.
* Prefer simple solutions.
* Keep code readable and maintainable.
* Consider security, testing and performance.
* Ask questions when requirements are unclear.

### Development Methodology

This project follows Specification-Driven Development (SDD).

Rules:

- Requirements drive the specification.
- The specification drives the implementation plan.
- The implementation plan drives task creation.
- Tasks drive implementation.
- Code must never become the source of truth.
- If implementation conflicts with the specification, the specification wins.
- Requirements and specifications must be updated before changing implementation behavior.
- No coding is allowed until requirements, specification, and plan have been reviewed and approved.

### Project Documents

Document the purpose of:

* requirements.md
* spec.md
* plan.md
* tasks.md
* README.md

### Add to Claude.md

Before implementing anything:

1. Verify requirements.md exists.
2. Verify spec.md exists.
3. Verify plan.md exists.
4. Verify the task appears in tasks.md.
5. Verify tests exist or create them.
6. Only then begin implementation.

If any of these are missing, stop and explain what is missing.
---

## Step 3 - Create spec-kit.constitution


Define project principles:

* Requirements first.
* Plan before implementation.
* Test before implementation.
* Simplicity over complexity.
* Security by default.
* Maintainability over cleverness.

## SDD First

This project follows Specification-Driven Development.

Every change must flow through:

Requirements
→ Specification
→ Plan
→ Tasks
→ Implementation

Implementation must never bypass this process.

---

## Step 4 - Create Skills

Location:

```text
.skills/
```

Every skill must contain:

### When To Use

Explain when Claude should invoke the skill.

### What To Check

Checklist of validations.

### What To Avoid

Common mistakes.

### Required Output

Expected review format.

Keep every skill:

* Small
* Reusable
* Generic
* Checklist based

---

## Required Skill: Testing

### Purpose

Validate testing quality.

### Check

* Happy paths
* Edge cases
* Error handling
* Return values
* Logging
* Test independence

### Avoid

* Testing implementation details
* Overly fragile tests

---

## Required Skill: Security

### Purpose

Validate security.

### Check

* OWASP Top 10 risks
* Input validation
* Authentication
* Authorization
* Secrets handling
* Sensitive data exposure

### Avoid

* Security assumptions
* Hardcoded secrets

---

## Required Skill: Performance

### Purpose

Validate performance.

### Check

* Complexity concerns
* Bottlenecks
* Expensive operations
* Memory usage

### Avoid

* Premature optimization

---

## Required Skill: Architecture

### Purpose

Validate architecture.

### Check

* Simplicity
* Separation of concerns
* Maintainability
* Scalability
* Consistency

### Avoid

* Overengineering

---

## Required Skill: Documentation & Logging

### Purpose

Validate documentation and logging.

### Check

* Useful logs
* Consistent format
* Documentation quality

### Avoid

* Sensitive information in logs
* Excessive logging

---

## Step 5 - Create Hooks

Create hooks for:

* Testing
* Logging
* Sensitive files (optional)

Update `claude.md` to reference all skills and hooks.

---

## Step 6 - Validate Skills

For every skill:

### Ask

* Does Claude actually use it?
* Is any instruction redundant?
* Is anything missing?

Update the skill if needed.

---

# PHASE 2 - STARTING A NEW ASSIGNMENT

---

## Step 1 - Import Assignment

Copy the assignment into the project.

Do not implement anything.

---

## Step 2 - Create Requirements Document

Create:

```text
requirements.md
```

Extract requirements from the assignment.

### Rules

* No implementation details.
* No assumptions.
* No extra features.

---

## Step 3 - Validate Requirements

Ask Claude:

> Verify that every assignment requirement appears in requirements.md and that no additional requirements were introduced.

Manually review results.

---

## Step 4 - Update claude.md

Add:

* Assignment summary.
* Important business context.
* Relevant constraints.

Keep it short.

---

## Step 5 - Run /specify

Generate project specification.

### Requirements

Claude should describe:

* What must be built.
* Why it must be built.
* Functional requirements.
* Non-functional requirements.
* Out-of-scope items.

### Forbidden

* Code
* Implementation details

---

## Step 6 - Run /clarify

Ask Claude to identify:

* Missing information
* Ambiguities
* Undefined behavior

### Rules

Only ask meaningful questions.

Update spec.md using the answers.

Do not:

* Expand scope
* Invent requirements

---

# PHASE 3 - PLANNING

---

## Step 1 - Create plan.md

Create:

```text
plan.md
```

The plan must include:

* Architecture
* Components
* Data flow
* Testing strategy
* Security considerations
* Performance considerations

### Rules

Keep it:

* Simple
* Clear
* Testable

### Forbidden

No implementation code.

---

## Step 2 - Validate Plan

Ask Claude:

> Verify that every requirement appears in the plan and that no unnecessary features were introduced.

---

## Step 3 - Run Skills Against plan.md

Run:

* Architecture Skill
* Security Skill
* Performance Skill
* Testing Skill

Verify:

* Simplicity
* Security
* Testability
* Clarity

Update plan.md if needed.

---

# PHASE 4 - TASK GENERATION

---

## Step 1 - Create tasks.md

Generate implementation tasks.

Requirements:

* Small
* Clear
* Ordered
* Traceable

---

## Step 2 - Validate Tasks

Verify:

* Every task maps to requirements.
* Every task maps to plan.md.
* No unnecessary tasks exist.

---

## Step 3 - Enforce TDD

The first implementation task should be:

> Create tests for planned behavior.

Before implementing any task:

* Verify tests exist.
* Create tests if needed.

---

## Step 4 - Add Review Tasks

Ensure tasks exist for:

* Security review
* Performance review
* Logging review
* Final validation

---

# PHASE 5 - IMPLEMENTATION

---

## Golden Rule

Implement one task at a time.

---

## For Every Task

### 1. Read Context

Read:

* claude.md
* requirements.md
* spec.md
* plan.md
* tasks.md

---

### 2. Identify Required Logic

Describe:

* What the task must do.
* What behavior changes.

---

### 3. Verify Tests

Check:

* Existing coverage
* Missing coverage

Add or update tests first.

---

### 4. Implement

Implement only the current task.

Do not:

* Add features
* Refactor unrelated code
* Expand scope

---

### 5. Execute Tests

Run relevant tests.

If failures exist:

* Fix
* Re-run

Repeat until green.

---

### 6. Complete Task

Mark task:

```text
DONE
```

Record:

* Files changed
* Tests created
* Tests updated
* Tests executed
* Requirements covered

---

# PHASE 6 - FINAL REVIEW

---

## Comprehensive Validation

Run all skills.

Verify:

### Requirements

* Everything was implemented.

### Scope

* No extra features exist.

### Testing

* Coverage is sufficient.
* Tests pass.

### Logging

* Logging exists where needed.
* No sensitive data is exposed.

### Security

* Security review passes.

### Architecture

* Simple
* Maintainable
* Understandable

### Performance

* No major bottlenecks

---

# PHASE 7 - DOCUMENTATION

---

## Create README.md

Include:

### Project Overview

What the project does.

### Setup

Installation instructions.

### Usage

How to run the application.

### Testing

How to run tests.

### Architecture

High-level architecture overview.

---

# PHASE 8 - DELIVERY

---

## Git Review

Before pushing:

* Tests pass.
* Documentation updated.
* Tasks completed.
* No debug code remains.

---

## Commit

Create meaningful commits.

---

## Push

Push final version to repository.

---

# OPTIONAL ADVANCED FEATURES

## Subagents

Consider using subagents for:

* Code review
* Security review
* Performance review
* Deep investigation

---

## MCP

Consider MCP for:

* External services
* APIs
* Tool integrations

---

## Hooks

Consider hooks for:

* Secret detection
* Sensitive files
* Test enforcement
* Logging validation

---

# WORKFLOW SUMMARY

Assignment
→ Requirements
→ Specification
→ Clarification
→ Plan
→ Plan Review
→ Tasks
→ Tests
→ Implementation
→ Final Review
→ README
→ Git Push

Never skip a phase.
Never implement before planning.
Never add features outside requirements.
