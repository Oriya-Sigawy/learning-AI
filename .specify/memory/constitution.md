<!--
Sync Impact Report
==================
Version change: (template / unversioned) → 1.0.0
Rationale: Initial ratification of the project constitution (MAJOR baseline).

Modified principles: N/A (initial adoption)
Added principles:
  - I. Requirements First
  - II. Plan Before Implementation
  - III. Test Before Implementation (NON-NEGOTIABLE)
  - IV. Simplicity Over Complexity
  - V. Security By Default
  - VI. Maintainability Over Cleverness
  - VII. Specification-Driven Development (SDD) First
Added sections:
  - Mandatory Review Gates
  - Development Workflow
  - Governance
Removed sections: N/A

Templates requiring updates:
  - .specify/templates/plan-template.md ✅ aligned (Constitution Check gate references this file)
  - .specify/templates/spec-template.md ✅ aligned (Requirements + Success Criteria are mandatory)
  - .specify/templates/tasks-template.md ⚠ pending — line 12 states tests are OPTIONAL, which
    conflicts with Principle III (TDD NON-NEGOTIABLE). Recommend making test tasks mandatory.

Follow-up TODOs: None.
-->

# learning-AI Constitution

## Core Principles

### I. Requirements First

All work MUST originate from explicit requirements.

The project MUST NOT:

- Implement assumptions.
- Infer new features.
- Expand scope without approval.

If requirements are unclear, work MUST stop and seek clarification before proceeding.

**Rationale**: Acting on unstated assumptions produces scope creep and rework. Explicit
requirements are the only authorized source of work.

### II. Plan Before Implementation

Implementation is NOT allowed until planning is complete.

Required workflow:

Requirements → Specification → Plan → Review → Tasks → Tests → Implementation

Production code MUST NOT be written before planning artifacts exist and have been reviewed.

**Rationale**: A reviewed plan catches design problems while they are cheap to fix and keeps
implementation traceable to intent.

### III. Test Before Implementation (NON-NEGOTIABLE)

The project follows Test-Driven Development (TDD).

Rules:

- Tests MUST be written before implementation.
- Tests MUST be derived from requirements and `plan.md`.
- Tests MUST validate behavior, not implementation details.
- New functionality MUST have tests before implementation begins.

Required workflow:

Plan → Tests → Verify Expected Failure → Implementation → Verify Tests Pass

**Rationale**: Writing tests first forces clear behavioral contracts and prevents code that is
untestable or untested from entering the project.

### IV. Simplicity Over Complexity

The simplest solution that satisfies the requirements MUST be preferred.

The project MUST avoid:

- Overengineering.
- Unnecessary abstractions.
- Premature optimization.
- Speculative design.

Complexity MUST be justified before it is introduced.

**Rationale**: As a small single-developer learning project, accidental complexity is the
primary risk to progress and understanding.

### V. Security By Default

Security MUST be considered during requirements, planning, implementation, and review.

Security reviews MUST cover:

- `requirements.md`
- `spec.md`
- `plan.md`
- implementation code

Security MUST be designed into the solution rather than added afterward.

**Rationale**: Retrofitting security is costly and error-prone; designing for it from the start
keeps the solution sound.

### VI. Maintainability Over Cleverness

Code MUST be understandable by future maintainers.

The project MUST prefer:

- Readability.
- Consistency.
- Clear naming.
- Straightforward design.

The project MUST avoid:

- Clever but obscure solutions.
- Unnecessary complexity.
- Hidden behavior.

A future maintainer SHOULD be able to understand the project quickly.

**Rationale**: Code is read far more often than it is written; clarity outlasts cleverness.

### VII. Specification-Driven Development (SDD) First

Every change MUST flow through:

Requirements → Specification → Plan → Tasks → Tests → Implementation

Implementation MUST NEVER bypass this process. When implementation conflicts with requirements,
specifications, or plans, the planning documents are the source of truth.

**Rationale**: A single authoritative pipeline keeps the project coherent and ensures the
documented intent—not ad hoc code—governs the system.

## Mandatory Review Gates

Every change MUST be reviewed against the following areas before it is considered complete. A
change MUST NOT be merged or accepted until each gate has been reviewed:

- **Security** — see Principle V.
- **Testing** — coverage and TDD compliance, see Principle III.
- **Architecture** — alignment with the approved plan and Principle IV (Simplicity).
- **Performance** — acceptable resource and runtime behavior for the change.
- **Logging** — adequate, non-sensitive logging to support debugging and observability.

## Development Workflow

The authorized end-to-end workflow is:

Requirements → Specification → Plan → Review → Tasks → Tests → Verify Expected Failure →
Implementation → Verify Tests Pass → Mandatory Review Gates

- No phase may be skipped.
- Tests MUST be observed failing before implementation begins.
- All Mandatory Review Gates MUST be satisfied before a change is closed.

## Governance

This constitution supersedes all other practices in the project. When any document, habit, or
tool conflicts with it, this constitution prevails.

- **Amendments**: Changes to this constitution MUST be documented, justified, and dated. Each
  amendment increments the version per the policy below.
- **Versioning policy** (semantic versioning):
  - **MAJOR**: Backward-incompatible governance or principle removals/redefinitions.
  - **MINOR**: A new principle or section is added, or guidance is materially expanded.
  - **PATCH**: Clarifications, wording, or non-semantic refinements.
- **Compliance review**: All work MUST be verified against these principles and the Mandatory
  Review Gates. Any complexity that deviates from Principle IV MUST be explicitly justified.

**Version**: 1.0.0 | **Ratified**: 2026-05-31 | **Last Amended**: 2026-05-31
