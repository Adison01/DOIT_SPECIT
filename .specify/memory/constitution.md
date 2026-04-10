<!--
Sync Impact Report
Version change: N/A -> 0.1.0
Modified principles: added Clean Code, Simple UX, Responsive Design, Minimal Dependencies, No-Testing Policy
Added sections: Technology, No-Testing Policy
Removed sections: None
Templates requiring updates: .specify/templates/plan-template.md (pending)
                          .specify/templates/spec-template.md (pending)
                          .specify/templates/tasks-template.md (pending)
                          .specify/templates/commands/* (pending)
Follow-up TODOs: Verify and update templates to reflect the No-Testing Policy and technology constraints.
-->

# Project Constitution — DOIT_SPECKIT

**Project:** DOIT_SPECKIT (doit-speckit)
**Ratification Date:** 2026-04-09
**Last Amended Date:** 2026-04-09
**Constitution Version:** 0.1.0

## Purpose
This constitution captures high-level, enforceable project governance and engineering principles for DOIT_SPECKIT. It is authoritative for topics declared below and is the primary reference used when updating project templates and guidance.

## Technology Constraint
React Required: The project MUST use React as declared in the repository `package.json` dependencies (doit-speckit depends on `react` and `react-dom`). Any new code or tooling must be compatible with React and its standard ecosystem.

## Principles

### 1. Clean Code
Statement: The codebase MUST be clear, maintainable, and self-explanatory. Code should prefer readability and correct intent over cleverness.

Rules: Functions and modules MUST have single responsibilities. Names MUST be descriptive. Complexity MUST be reduced via small, well-scoped abstractions.

Rationale: Clear code reduces onboarding time, lowers defect risk, and enables rapid iteration.

### 2. Simple UX
Statement: User interfaces MUST be simple, predictable, and focused on primary user tasks.

Rules: UI flows MUST minimize choices required to complete primary tasks. Interactions MUST avoid surprises and provide clear affordances and feedback.

Rationale: Simplicity increases usability and reduces support overhead.

### 3. Responsive Design
Statement: The UI MUST adapt gracefully across common device sizes and input modes (touch, mouse, keyboard).

Rules: Layouts MUST be fluid or use breakpoints that preserve core functionality. Critical UI elements MUST remain accessible on small screens.

Rationale: A responsive UI broadens the user base and ensures functional parity across devices.

### 4. Minimal Dependencies
Statement: The project MUST minimize third-party dependencies to reduce maintenance and security surface area.

Rules: New dependencies MUST be justified in writing (short rationale and alternatives considered). Prefer lightweight, well-maintained libraries with permissive licenses.

Rationale: Fewer dependencies lower upgrade burden and improve stability.

### 5. No-Testing Policy (Project Rule — Non-negotiable)
Statement: This project MUST NOT include unit tests, integration tests, or end-to-end tests. No test frameworks, test scripts, or test-related CI steps shall be added to the repository.

Rules: Any existing or proposed test code, test directories, or CI steps that introduce testing MUST be removed or prevented. Documentation and automation MUST NOT reference test execution or test requirements. This rule supersedes other guidance that would introduce testing obligations.

Rationale: The project has explicitly chosen to exclude testing from the development workflow; governance and templates will reflect this constraint.

## Governance
Amendments: Amendments to this constitution require an explicit amendment proposal file in .specify/amendments/ describing the change, rationale, and migration plan. Amendments MUST include an explicit version bump rationale.

Versioning Policy: The Constitution Version follows semantic-like increments for governance: MAJOR for incompatible principle removals/renames, MINOR for adding new principles or materially expanding guidance, PATCH for wording/clarity fixes. This update is initial adoption: 0.1.0.

Compliance: Contributors MUST follow the principles. Where automated checks exist (linters, build), they SHOULD validate coding style and tech constraints but MUST NOT introduce test execution steps.

## Compliance & Tooling Guidance
Linting and Formatting: Use linters and formatters to enforce Clean Code without introducing tests. Linting is encouraged and permitted.

CI/CD: CI pipelines MAY perform builds, linting, type checks, and previews. CI MUST NOT run tests or include test-related steps.

Templates: Project templates and scaffolding MUST be updated to enforce React as the runtime, avoid adding test scaffolds, and include guidance consistent with the principles above.

## Change Log
2026-04-09 (0.1.0): Initial constitution adopted with principles: Clean Code, Simple UX, Responsive Design, Minimal Dependencies, and a No-Testing Policy. Technology constraint: React required.

## Contact
Maintainership and amendment requests: create an issue or open an amendment file in .specify/amendments/.


