# Feature Specification: Initial Page Setup

**Feature Branch**: `001-initial-page-setup`  
**Created**: 2026-04-09  
**Status**: Draft  
**Input**: User description: "initial page setup-this application should be a goal tracking web app called 'doit'. There should be two columns - a left one where current goals are shown, along with how many days left the user has to achieve the goal, and a right one where completed goals are. Each goal can be 'checked' using a checkbox, and then either moved to the completed column or permanently deleted. To add new goals, a user can click on a button to open a new goal form in a modal ( title and end date fields). Goals reaching their end date (within 3 days) are highlighted. Lets use a modern light theme with fun pastel colours."

## User Scenarios & Testing (mandatory)

### User Story 1 - View Goals (Priority: P1)
As a user, I want to see my active goals on the left and completed goals on the right so I can track progress at a glance.

**Why this priority**: Core visibility and value of the app — without this the app has no utility.

**Independent Test**: Open the app and confirm the left column lists active goals with days remaining and the right column lists completed goals.

**Acceptance Scenarios**:
1. Given the app has at least one active goal, When the user opens the page, Then the left column displays each active goal with title and days left.
2. Given the app has completed goals, When the user opens the page, Then the right column displays completed goals ordered by completion date.

---

### User Story 2 - Mark Complete or Delete (Priority: P1)
As a user, I want to check a goal and either move it to completed or delete it permanently, so I can keep my workspace tidy.

**Independent Test**: Check a goal's checkbox and confirm you can choose to move it to completed or delete it; verify UI updates.

**Acceptance Scenarios**:
1. Given an active goal, When the user checks the goal and selects "Complete", Then the goal moves to the completed column and shows completion date.
2. Given an active goal, When the user checks the goal and selects "Delete", Then the goal is permanently removed from both columns.

---

### User Story 3 - Add Goal (Priority: P1)
As a user, I want to add a new goal via a modal form with title and end date so I can track new items quickly.

**Independent Test**: Click the "Add Goal" button, fill title and end date in the modal, submit, and confirm the new goal appears in the left column.

**Acceptance Scenarios**:
1. Given the user clicks "Add Goal", When the modal opens and the user submits valid title and end date, Then the new goal appears in the active column with correct days-left calculation.
2. Given the user submits an end date that is today or in the past, When the form is submitted, Then show a validation error and prevent submission.

---

### User Story 4 - Highlight Near-Expiry (Priority: P2)
As a user, I want goals with three or fewer days remaining to be visually highlighted so urgent goals stand out.

**Independent Test**: Create or identify a goal with <= 3 days left and confirm highlight style appears.

**Acceptance Scenarios**:
1. Given a goal with 3 or fewer days left, When displayed in the active column, Then it is visually highlighted using the theme's warning accent.

---

### Edge Cases

- What happens if the user's clock/timezone changes near midnight? The days-left calculation should use date-only arithmetic (local date) to avoid negative off-by-one surprises.
- If the user adds a goal without an end date, the UI must prevent submission (validation rule).
- If there are many goals, the columns should scroll independently and preserve ordering and visual affordances.

## Requirements (mandatory)

### Functional Requirements

- **FR-001**: System MUST display active goals in the left column and completed goals in the right column.
- **FR-002**: Each goal record MUST show `title`, `end date`, and computed `days left` for active goals, and `completion date` for completed goals.
- **FR-003**: Users MUST be able to check a goal using a checkbox and choose to `Complete` or `Delete` that goal.
- **FR-004**: Users MUST be able to add a new goal via a modal form with `title` (required) and `end date` (required).
- **FR-005**: Goals with `days left` <= 3 MUST be visually highlighted.
- **FR-006**: The UI MUST use a modern light theme with fun pastel colours and be responsive across device widths.
- **FR-007**: The app MUST persist goals between page reloads (MVP: local browser storage; later: optional server persistence).
- **FR-008**: Input validation: Title MUST be non-empty; end date MUST be a future date.

### Key Entities

- **Goal**: Represents a user's goal.
  - Attributes: `id` (string), `title` (string), `endDate` (ISO date), `createdAt` (ISO date), `completed` (boolean), `completedAt` (ISO date|null)

## Success Criteria (mandatory)

### Measurable Outcomes

- **SC-001**: Users can add a new goal and see it appear in the active column within 2 seconds of submission.
- **SC-002**: Users can mark a goal complete or delete it and observe the UI update within 1 second.
- **SC-003**: 95% of users see near-expiry goals visually highlighted as expected when `days left` <= 3 (as verified during manual review).
- **SC-004**: The UI remains usable and layout intact on common viewports (mobile portrait, tablet, desktop) with no critical overlaps.

## Assumptions

- Persistence: MVP will use browser local storage for goals; server-side persistence is out of scope for initial page setup.
- Authentication: The app is single-user for v1 (no accounts). Multi-user sync is out of scope.
- Timezone: Days-left calculation uses the user's local date and treats end date inclusively.
- Accessibility: Basic keyboard focus and labels are included, but full WCAG conformance is out of scope for v1.
