# Risk Register

## 1. Purpose

This document identifies the main risks related to the project **“Design and Development of a Web-Based Car Service Booking and Management System.”**

Each risk is evaluated using:

- Probability
- Impact
- Priority
- Mitigation
- Contingency

Probability levels:

- Low
- Medium
- High

Impact levels:

- Low
- Medium
- High

---

# 2. Risk Summary

The main project risks include:

- insufficient development time;
- incomplete core functionality;
- integration problems;
- database errors;
- authentication or authorization issues;
- booking logic defects;
- Git workflow conflicts;
- inconsistent documentation;
- team availability problems;
- UX implementation delays;
- testing delays;
- Docker and environment configuration issues.

---

# 3. Risk Register

## RISK-01 — Insufficient Development Time

**Probability:** High  
**Impact:** High  
**Priority:** Critical

### Description

The project includes frontend, backend, database, authentication, booking logic, dashboards, testing, and documentation.

Limited development time may prevent completion of all planned functionality.

### Mitigation

- Prioritize Must Have requirements.
- Complete the end-to-end MVP before optional functionality.
- Use YouTrack to track progress.
- Divide work into small tasks.
- Avoid spending excessive time on optional design improvements.

### Contingency

If time becomes limited:

- postpone online payments;
- postpone reminders;
- postpone multimedia attachments;
- postpone advanced analytics;
- focus only on the core booking workflow.

---

## RISK-02 — Core Booking Workflow Is Not Completed

**Probability:** Medium  
**Impact:** High  
**Priority:** Critical

### Description

The main value of the project depends on the complete workflow:

`Customer → Booking → Admin → Mechanic → Completed Service → Service History`

If one part is missing, the final demonstration may be incomplete.

### Mitigation

Develop the workflow in this order:

1. Authentication
2. Vehicle management
3. Service catalogue
4. Booking creation
5. Admin confirmation
6. Mechanic assignment
7. Service status updates
8. Service history

### Contingency

Reduce secondary functionality and focus development resources on completing the end-to-end flow.

---

## RISK-03 — Frontend and Backend Integration Problems

**Probability:** Medium  
**Impact:** High  
**Priority:** High

### Description

The React frontend and Go backend may use inconsistent:

- endpoint paths;
- request formats;
- response structures;
- authentication headers;
- status values.

### Mitigation

- Define REST endpoints clearly.
- Use consistent JSON structures.
- Test endpoints using Postman before frontend integration.
- Document important API contracts.
- Use TypeScript interfaces for frontend API data.

### Contingency

Fix integration one module at a time, starting with authentication and booking.

---

## RISK-04 — Database Model Problems

**Probability:** Medium  
**Impact:** High  
**Priority:** High

### Description

Incorrect database relationships may create problems between:

- Users
- Vehicles
- Services
- Bookings
- Mechanics
- Service History

### Mitigation

- Design models before implementing complex API logic.
- Use PostgreSQL foreign keys.
- Test GORM relationships.
- Validate ownership in backend logic.
- Use test data during development.

### Contingency

Simplify the schema if necessary while preserving the core relationships required by the project.

---

## RISK-05 — Booking Conflicts or Double Booking

**Probability:** Medium  
**Impact:** High  
**Priority:** Critical

### Description

Two customers may attempt to book incompatible overlapping appointments.

This would directly contradict one of the main project objectives.

### Mitigation

- Perform availability checks on the backend.
- Consider service duration when checking slots.
- Validate availability immediately before creating a booking.
- Add automated or manual conflict test cases.

### Contingency

If advanced resource scheduling is too complex, use a simplified time-slot model while still preventing duplicate reservations for the same slot.

---

## RISK-06 — Authentication Security Defects

**Probability:** Medium  
**Impact:** High  
**Priority:** Critical

### Description

Incorrect authentication implementation may allow unauthorized access or expose user credentials.

### Mitigation

- Hash passwords.
- Use JWT authentication.
- Validate tokens on protected endpoints.
- Keep JWT secrets outside the repository.
- Test invalid and expired tokens.

### Contingency

Disable affected endpoints until authentication checks are corrected.

---

## RISK-07 — Incorrect Role-Based Authorization

**Probability:** Medium  
**Impact:** High  
**Priority:** Critical

### Description

A Customer or Mechanic may gain access to restricted functionality if role checks are not correctly implemented.

### Mitigation

- Implement role checks in backend middleware.
- Do not rely only on hidden frontend buttons.
- Test each protected endpoint using all three roles.

### Contingency

Restrict affected API routes until authorization logic is corrected.

---

## RISK-08 — Loss or Corruption of Project Work

**Probability:** Low  
**Impact:** High  
**Priority:** High

### Description

Local files may be lost or changed incorrectly.

Possible causes include:

- accidental deletion;
- incorrect Git commands;
- local disk problems;
- OneDrive synchronization problems.

### Mitigation

- Push work to GitHub regularly.
- Use separate branches.
- Commit meaningful changes frequently.
- Keep `main` stable.
- Avoid storing the only copy of work locally.

### Contingency

Restore work from GitHub commit history or merged Pull Requests.

---

## RISK-09 — Git Merge Conflicts

**Probability:** Medium  
**Impact:** Medium  
**Priority:** Medium

### Description

Both team members may edit the same files or work on outdated local branches.

### Mitigation

Before creating a new branch:

```text
git checkout main
git pull origin main
```

Use separate task branches and avoid editing the same document simultaneously.

### Contingency

Resolve conflicts manually and verify the affected files before committing the merge.

---

## RISK-10 — Team Member Availability

**Probability:** Medium  
**Impact:** Medium  
**Priority:** High

### Description

One team member may temporarily be unavailable because of university workload, personal schedule, or other obligations.

### Mitigation

- Store all work in GitHub.
- Document tasks in YouTrack.
- Keep responsibilities visible.
- Avoid keeping important project knowledge only with one team member.

### Contingency

The available team member continues critical tasks and reassigns lower-priority work when necessary.

---

## RISK-11 — Documentation Becomes Inconsistent With Implementation

**Probability:** Medium  
**Impact:** Medium  
**Priority:** Medium

### Description

Requirements and diagrams may no longer match the actual implementation after technical changes.

### Mitigation

- Update documentation after major implementation decisions.
- Review diagrams before final submission.
- Compare implemented functionality with requirements.

### Contingency

Update documentation to accurately reflect the final system rather than preserving outdated planned functionality.

---

## RISK-12 — UX Prototype Differs From Final Frontend

**Probability:** High  
**Impact:** Low  
**Priority:** Low

### Description

The final React interface may not exactly match the initial UX prototype.

### Mitigation

Use the prototype primarily to preserve:

- navigation;
- required screens;
- core user flows;
- information structure.

### Contingency

Allow visual design changes as long as the main workflow and requirements remain consistent.

---

## RISK-13 — Testing Is Delayed Until the End

**Probability:** Medium  
**Impact:** High  
**Priority:** High

### Description

If testing begins only after development is complete, critical defects may be discovered too late.

### Mitigation

- Test API endpoints during development.
- Execute relevant test cases after each module.
- Verify authentication before building dependent functionality.
- Test booking conflicts early.

### Contingency

Prioritize the critical test set defined in the verification plan.

---

## RISK-14 — Docker Environment Problems

**Probability:** Medium  
**Impact:** Medium  
**Priority:** Medium

### Description

Docker containers may fail because of:

- incorrect environment variables;
- port conflicts;
- database startup order;
- configuration errors.

### Mitigation

- Keep Docker configuration simple.
- Document environment variables.
- Test Docker Compose regularly.
- Use consistent development ports.

### Contingency

For demonstration, run frontend, backend, and PostgreSQL separately if the Docker environment cannot be repaired in time.

---

## RISK-15 — PostgreSQL Connection Failure

**Probability:** Medium  
**Impact:** High  
**Priority:** High

### Description

The backend may fail to connect to PostgreSQL because of incorrect:

- host;
- port;
- username;
- password;
- database name.

### Mitigation

- Use environment variables.
- Maintain an example environment configuration.
- Verify database connectivity when the backend starts.

### Contingency

Use a verified local PostgreSQL configuration for demonstration.

---

## RISK-16 — Scope Creep

**Probability:** High  
**Impact:** Medium  
**Priority:** High

### Description

The team may attempt to add too many features before completing the MVP.

Examples include:

- payment integration;
- WhatsApp;
- inventory;
- advanced statistics;
- multi-location support;
- multimedia attachments.

### Mitigation

Follow the requirement priorities:

- Must Have first
- Should Have second
- Could Have only after the MVP works

### Contingency

Remove optional functionality from the current development cycle.

---

# 4. Risk Priority Summary

## Critical Risks

- RISK-01 — Insufficient Development Time
- RISK-02 — Incomplete Core Workflow
- RISK-05 — Booking Conflicts
- RISK-06 — Authentication Security
- RISK-07 — Role Authorization

These risks require the highest attention.

---

## High Risks

- RISK-03 — Integration Problems
- RISK-04 — Database Model Problems
- RISK-08 — Loss of Project Work
- RISK-10 — Team Availability
- RISK-13 — Testing Delays
- RISK-15 — PostgreSQL Connection Failure
- RISK-16 — Scope Creep

---

## Medium / Low Risks

- Git merge conflicts
- Documentation inconsistency
- Docker configuration problems
- UX visual differences

These risks should still be monitored but are less likely to prevent completion of the core project.

---

# 5. Risk Monitoring

Risks should be reviewed during project development.

The team should monitor:

- milestone progress;
- unfinished Must Have requirements;
- critical bugs;
- GitHub activity;
- test results;
- team workload.

If a risk increases in probability or impact, its priority and mitigation actions should be reviewed.

---

# 6. Conclusion

The highest project risks are related to:

- development time;
- completion of the core booking workflow;
- booking correctness;
- authentication;
- authorization;
- frontend/backend integration.

The project reduces these risks by prioritizing the MVP, using progressive Git development, defining test cases early, and postponing optional functionality until the main workflow is complete.