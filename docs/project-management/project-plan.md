# Project Management Plan

## 1. Project Overview

**Project Title:**  
Design and Development of a Web-Based Car Service Booking and Management System

**Team Members:**

- Danial Makazhanov
- Madi Qanatuly

The project aims to design and develop a web-based system that allows customers to book car service appointments online and allows mechanics and administrators to manage service operations.

The system will support three main roles:

- Customer
- Mechanic
- Admin

---

# 2. Project Objectives

The main objectives of the project are:

- provide online booking for car service appointments;
- allow customers to manage their vehicles;
- display available services, prices, and estimated duration;
- prevent booking conflicts;
- provide booking status tracking;
- support mechanic job management;
- support administrator booking and service management;
- maintain vehicle service history;
- provide a structured and maintainable web architecture.

---

# 3. Development Stages

The project will be divided into the following main stages.

## Stage 1 — Problem Analysis and Research

Main activities:

- define the problem;
- identify target users;
- conduct user interviews;
- review academic literature;
- analyze existing systems.

Expected result:

A validated understanding of the problem and user needs.

---

## Stage 2 — Requirements Definition

Main activities:

- define functional requirements;
- define non-functional requirements;
- prioritize requirements;
- define acceptance criteria;
- create requirements traceability.

Expected result:

A structured requirements specification.

---

## Stage 3 — Architecture and Technology Design

Main activities:

- compare technical alternatives;
- select project technologies;
- create System Context Diagram;
- create Use Case Diagram;
- create Component Diagram;
- define frontend/backend/database interaction.

Expected result:

A clear system architecture and selected technology stack.

---

## Stage 4 — UX Design

Main activities:

- create customer interface prototype;
- create mechanic interface prototype;
- create admin interface prototype;
- define main user flows.

Expected result:

An initial UX prototype representing the core workflows.

---

## Stage 5 — Backend Development

Main activities:

- initialize Go backend;
- configure Gin;
- configure PostgreSQL;
- configure GORM;
- implement database models;
- implement JWT authentication;
- implement role authorization;
- implement vehicle API;
- implement service API;
- implement booking API;
- implement mechanic workflow;
- implement admin operations.

Expected result:

A functional REST backend.

---

## Stage 6 — Frontend Development

Main activities:

- initialize React + TypeScript frontend;
- configure Tailwind CSS;
- implement authentication pages;
- implement Customer dashboard;
- implement vehicle management;
- implement service catalogue;
- implement booking flow;
- implement booking management;
- implement service history;
- implement Mechanic dashboard;
- implement Admin dashboard.

Expected result:

A functional web interface connected to the backend.

---

## Stage 7 — Integration

Main activities:

- connect frontend to REST API;
- integrate JWT authentication;
- verify role-based access;
- connect booking workflow;
- verify database operations;
- configure Docker environment.

Expected result:

An integrated web application.

---

## Stage 8 — Testing and Evaluation

Main activities:

- execute functional test cases;
- test API endpoints;
- test authentication;
- test role-based authorization;
- test booking conflicts;
- test booking status workflow;
- verify service history;
- perform basic performance checks;
- fix identified defects.

Expected result:

A tested implementation that satisfies the core requirements.

---

## Stage 9 — Final Documentation and Demonstration

Main activities:

- update project documentation;
- prepare screenshots;
- prepare final diagrams;
- prepare testing evidence;
- prepare demonstration scenario;
- prepare presentation and defense materials.

Expected result:

A complete project package ready for final defense.

---

# 4. Project Milestones

## Milestone 1 — Research Completed

Includes:

- Project Proposal
- User Interviews
- Literature Review
- Existing Systems Comparison

Status:

Completed.

---

## Milestone 2 — Requirements and Architecture Completed

Includes:

- Technology Comparison
- Functional Requirements
- Non-Functional Requirements
- System Context Diagram
- Use Case Diagram
- Component Diagram

Status:

Completed.

---

## Milestone 3 — UX and Verification Planning Completed

Includes:

- UX Prototype
- Verification Plan
- Test Cases
- Evaluation Criteria

Status:

Completed.

---

## Milestone 4 — Backend Core

Target result:

- authentication;
- users;
- vehicles;
- services;
- bookings;
- database integration.

---

## Milestone 5 — Main Frontend

Target result:

- authentication pages;
- customer dashboard;
- vehicle management;
- service catalogue;
- booking workflow.

---

## Milestone 6 — Mechanic and Admin Functions

Target result:

- mechanic job management;
- booking status updates;
- admin booking management;
- mechanic assignment;
- service management.

---

## Milestone 7 — Integrated MVP

Target result:

A working end-to-end workflow:

`Customer → Booking → Admin → Mechanic → Completed Service → Service History`

---

## Milestone 8 — Tested Final Version

Target result:

- critical test cases pass;
- critical defects are fixed;
- documentation is updated;
- final demonstration is ready.

---

# 5. Team Responsibilities

## Danial Makazhanov

Main responsibilities:

- project documentation;
- requirements analysis;
- backend development support;
- API testing;
- system testing;
- GitHub documentation;
- project research.

---

## Madi Qanatuly

Main responsibilities:

- architecture documentation;
- UX prototype;
- frontend development support;
- project management documentation;
- testing support;
- GitHub workflow.

---

## Shared Responsibilities

Both team members participate in:

- technical decisions;
- integration;
- testing;
- code review;
- documentation review;
- final presentation;
- system demonstration.

Responsibilities may be adjusted depending on implementation progress and workload.

---

# 6. Development Workflow

The project uses the following workflow:

1. Create a YouTrack task.
2. Update local `main`.
3. Create a dedicated Git branch.
4. Implement the required change.
5. Create meaningful commits.
6. Push the branch to GitHub.
7. Create a Pull Request.
8. Review the change.
9. Merge into `main`.
10. Mark the YouTrack task as Done.

Example:

`DIP-10 → DIP-10-project-management → commits → Pull Request → main`

---

# 7. Version Control Strategy

The `main` branch represents the stable project state.

Development should normally occur in separate branches.

Example branch names:

- `DIP-7-architecture-diagrams`
- `DIP-8-ux-prototype`
- `DIP-9-verification-plan`
- `feature-authentication`
- `feature-booking`
- `feature-admin-dashboard`

Commit messages should clearly describe the change.

Example:

`DIP-10: Add project management plan`

---

# 8. Project Tracking

YouTrack is used to track:

- tasks;
- task status;
- responsibility;
- development progress.

Main workflow:

`To Do → In Progress → Done`

GitHub provides technical evidence of development progress through:

- branches;
- commits;
- Pull Requests;
- merged changes.

---

# 9. Definition of Done

A task can be considered complete when:

- the required work is finished;
- related documentation or code is added;
- changes are committed;
- changes are pushed to GitHub;
- Pull Request is created where applicable;
- changes are merged into `main`;
- YouTrack task is moved to Done.

---

# 10. Core MVP Definition

The Minimum Viable Product must demonstrate the following end-to-end workflow:

1. Customer registers or logs in.
2. Customer adds or selects a vehicle.
3. Customer views services.
4. Customer selects an available appointment.
5. Customer creates a booking.
6. Admin confirms the booking.
7. Admin assigns a mechanic.
8. Mechanic starts the service.
9. Mechanic completes the service.
10. Completed service appears in vehicle service history.

This workflow has the highest development priority.

---

# 11. Lower-Priority Features

The following functions can be developed after the core MVP:

- booking rescheduling;
- advanced dashboard statistics;
- automatic reminders;
- multimedia attachments;
- online payment;
- inventory management;
- multi-location support.

These functions should not delay completion of the core booking workflow.

---

# 12. Progress Monitoring

Project progress will be monitored using:

- YouTrack task status;
- GitHub commit history;
- Pull Requests;
- completed requirements;
- completed test cases;
- milestone completion.

The team should regularly compare development progress against the defined MVP and project milestones.

---

# 13. Project Completion Criteria

The project is considered ready for final demonstration when:

- core Must Have requirements are implemented;
- the main end-to-end workflow works;
- critical security requirements are satisfied;
- critical test cases pass;
- no blocking defect prevents demonstration;
- documentation reflects the implemented system;
- the repository contains a clear development history.

---

# 14. Conclusion

The project management plan defines a structured development process from research and requirements through implementation, testing, and final demonstration.

The project prioritizes completion of the core booking workflow before optional functionality.

YouTrack and GitHub provide traceability between planned work and actual project progress.