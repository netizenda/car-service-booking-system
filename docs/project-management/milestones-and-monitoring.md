# Milestones and Project Monitoring

## 1. Purpose

This document defines the project milestones, checkpoints, and progress monitoring approach for the project **“Design and Development of a Web-Based Car Service Booking and Management System.”**

The purpose is to ensure that the team can track progress and identify delays before they affect the final project delivery.

---

# 2. Main Project Milestones

## Milestone 1 — Research and Problem Validation

### Deliverables

- Project Proposal
- User Interviews
- Literature Review
- Existing Systems Comparison

### Completion Criteria

This milestone is complete when:

- the project problem is clearly defined;
- target users are identified;
- user needs are supported by interview evidence;
- relevant academic literature is reviewed;
- existing automotive service systems are compared.

### Status

Completed.

---

## Milestone 2 — Requirements Definition

### Deliverables

- Functional Requirements
- Non-Functional Requirements
- Requirement Priorities
- Acceptance Criteria
- Requirements Traceability

### Completion Criteria

This milestone is complete when:

- core requirements have unique IDs;
- Customer, Mechanic, and Admin requirements are defined;
- Must Have and optional requirements are separated;
- mandatory requirements have acceptance criteria;
- requirements can be verified through testing.

### Status

Completed.

---

## Milestone 3 — Technology and Architecture Design

### Deliverables

- Technology Comparison
- Technology Decision Summary
- System Context Diagram
- Use Case Diagram
- Component Diagram

### Completion Criteria

This milestone is complete when:

- reasonable technology alternatives are compared;
- the selected stack is justified;
- system boundaries are defined;
- main use cases are represented;
- major technical components are represented.

### Status

Completed.

---

## Milestone 4 — UX Prototype

### Deliverables

- Customer UX Flow
- Mechanic Dashboard Prototype
- Admin Dashboard Prototype
- UX Prototype Overview

### Completion Criteria

This milestone is complete when the prototype demonstrates:

- customer booking flow;
- vehicle management;
- service catalogue;
- booking management;
- mechanic workflow;
- admin workflow.

### Status

Completed.

---

## Milestone 5 — Verification Planning

### Deliverables

- Verification and Evaluation Plan
- Test Cases
- Evaluation Criteria

### Completion Criteria

This milestone is complete when:

- functional testing is defined;
- security testing is defined;
- role-based access testing is defined;
- booking conflict testing is defined;
- critical test cases are identified;
- success criteria are documented.

### Status

Completed.

---

# 3. Future Development Milestones

## Milestone 6 — Backend Foundation

### Main Tasks

- initialize Go project;
- configure Gin;
- connect PostgreSQL;
- configure GORM;
- create initial database models;
- create basic REST API structure.

### Checkpoint

The backend can start successfully and connect to PostgreSQL.

---

## Milestone 7 — Authentication and Authorization

### Main Tasks

- registration;
- login;
- password hashing;
- JWT creation;
- JWT validation;
- Customer, Mechanic, and Admin authorization.

### Checkpoint

The following must work:

- valid login;
- invalid login rejection;
- protected API endpoints;
- role-based endpoint restrictions.

---

## Milestone 8 — Customer Core Functions

### Main Tasks

- My Cars;
- service catalogue;
- available time slots;
- booking creation;
- My Bookings;
- booking cancellation.

### Checkpoint

A Customer can complete:

`Login → Vehicle → Service → Date → Time → Booking`

---

## Milestone 9 — Admin Core Functions

### Main Tasks

- view bookings;
- confirm bookings;
- assign mechanics;
- manage services;
- manage users;
- view daily schedule.

### Checkpoint

Admin can process a newly created Customer booking and assign it to a Mechanic.

---

## Milestone 10 — Mechanic Core Functions

### Main Tasks

- view assigned jobs;
- view daily jobs;
- start service;
- add comments;
- complete service.

### Checkpoint

Mechanic can complete:

`Confirmed → In Progress → Completed`

---

## Milestone 11 — Service History

### Main Tasks

- store completed service information;
- connect service history to vehicle;
- display service history to Customer.

### Checkpoint

A completed mechanic job appears in the correct vehicle's service history.

---

## Milestone 12 — End-to-End MVP

### Required Workflow

`Customer`

`↓`

`Vehicle`

`↓`

`Service`

`↓`

`Available Slot`

`↓`

`Booking`

`↓`

`Admin Confirmation`

`↓`

`Mechanic Assignment`

`↓`

`In Progress`

`↓`

`Completed`

`↓`

`Service History`

### Checkpoint

The complete workflow works without manually changing database records.

---

## Milestone 13 — Testing and Stabilization

### Main Tasks

- execute critical test cases;
- fix authorization defects;
- fix booking conflicts;
- test invalid inputs;
- test API responses;
- verify service history;
- check basic performance.

### Checkpoint

All critical test cases pass.

---

## Milestone 14 — Final Demonstration Preparation

### Main Tasks

- update screenshots;
- update README;
- update diagrams if implementation changed;
- prepare Postman evidence;
- prepare demo data;
- prepare presentation;
- rehearse demonstration.

### Checkpoint

The team can demonstrate the full MVP from start to finish.

---

# 4. Weekly Progress Monitoring

Project progress should be reviewed regularly.

The team should check:

- open YouTrack tasks;
- completed YouTrack tasks;
- Pull Requests;
- recent commits;
- unfinished Must Have requirements;
- failed test cases;
- critical risks.

A short progress review should answer:

1. What was completed?
2. What is currently in progress?
3. What is blocked?
4. What is the highest-priority next task?
5. Has any project risk increased?

---

# 5. GitHub Monitoring

GitHub should provide evidence of progressive project development.

The team should monitor:

- active branches;
- commit history;
- Pull Requests;
- merged changes;
- repository structure.

Development should not appear as one large final upload.

Instead, the repository should demonstrate continuous progress through meaningful commits.

---

# 6. YouTrack Monitoring

YouTrack is used as the main task tracking tool.

Each significant task should contain:

- clear title;
- description;
- acceptance criteria;
- assignee;
- current stage.

Typical workflow:

`To Do → In Progress → Done`

Where appropriate, task IDs should be referenced in:

- branch names;
- commit messages;
- Pull Requests.

---

# 7. Requirement Monitoring

The team should periodically review the Must Have requirements.

Important questions:

- Is the requirement implemented?
- Is it partially implemented?
- Is it not started?
- Has it been tested?
- Did the test pass?

Priority should always be given to incomplete Must Have requirements before optional features.

---

# 8. Testing Monitoring

Test execution status can be classified as:

- Not Run
- Pass
- Fail
- Blocked

Critical failed tests should receive immediate attention.

Examples include:

- authentication failure;
- role authorization failure;
- booking conflict failure;
- broken booking workflow;
- incorrect service history.

---

# 9. Risk Monitoring

The project risk register should be reviewed during development.

Critical risks include:

- insufficient development time;
- incomplete core workflow;
- double booking;
- authentication defects;
- authorization defects.

If one of these risks increases, the team should reduce lower-priority work and focus on the MVP.

---

# 10. Pre-Defense Checkpoint

Before pre-defense, the team should verify that the repository contains:

- proposal documentation;
- interview evidence;
- literature review;
- existing systems comparison;
- technology comparison;
- requirements;
- architecture diagrams;
- UX prototype;
- verification plan;
- project management documentation;
- risk documentation;
- supervisor feedback.

GitHub should also contain:

- progressive commits;
- task branches;
- Pull Requests;
- organized documentation;
- README.

---

# 11. Final Defense Checkpoint

Before final defense, the team should verify:

- MVP is functional;
- authentication works;
- authorization works;
- booking conflicts are prevented;
- Customer flow works;
- Admin flow works;
- Mechanic flow works;
- service history works;
- critical test cases pass;
- project documentation matches the implementation;
- demonstration scenario has been tested.

---

# 12. Progress Escalation

If the project falls behind schedule:

1. Stop optional feature development.
2. Review unfinished Must Have requirements.
3. Identify the blocked core workflow step.
4. Assign team effort to the blocker.
5. Complete the MVP before returning to secondary features.

Optional functionality should never prevent completion of the core system.

---

# 13. Conclusion

The project will be monitored through milestones, YouTrack tasks, GitHub activity, requirement completion, test results, and risk status.

The main measure of progress is not the number of features implemented, but whether the project is moving toward a complete and testable end-to-end MVP.