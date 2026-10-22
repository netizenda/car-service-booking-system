# Evaluation Criteria

## 1. Purpose

This document defines the criteria that will be used to evaluate whether the project **“Design and Development of a Web-Based Car Service Booking and Management System”** satisfies its main objectives and is ready for demonstration.

The evaluation focuses on:

- completion of core functional requirements;
- successful execution of critical test cases;
- security and access control;
- booking workflow correctness;
- reliability;
- usability;
- traceability between requirements and verification results.

---

# 2. Evaluation Approach

The system will be evaluated using:

- functional test results;
- API testing;
- manual browser testing;
- role-based access tests;
- database verification;
- performance checks;
- demonstration of the complete user workflow.

The project will be considered successful when the core system functions correctly and no critical defect prevents demonstration of the main workflow.

---

# 3. Core Success Criteria

## EC-01 — Authentication Works Correctly

The system must allow valid users to authenticate successfully.

Success conditions:

- valid credentials are accepted;
- invalid credentials are rejected;
- protected endpoints require authentication;
- authentication tokens are validated correctly.

Related test cases:

- TC-03
- TC-04
- TC-05
- TC-39
- TC-40

**Required Result:** Pass

---

## EC-02 — Role-Based Access Is Enforced

Customer, Mechanic, and Admin functionality must be separated.

Success conditions:

- Customer cannot access Admin functions;
- Customer cannot access Mechanic-only functions;
- Mechanic cannot access Admin functions;
- Admin can access authorized administrative functions.

Related test cases:

- TC-06
- TC-07
- TC-08

**Required Result:** Pass

---

## EC-03 — Customer Data Is Isolated

Customers must only access their own vehicles and bookings.

Success conditions:

- another customer's vehicle cannot be accessed;
- another customer's booking cannot be modified;
- ownership checks are performed by the backend.

Related test cases:

- TC-11
- TC-21

**Required Result:** Pass

---

## EC-04 — Vehicle Management Works

The Customer must be able to manage their vehicles.

Success conditions:

- vehicle can be created;
- own vehicles can be viewed;
- vehicle information can be edited;
- unauthorized vehicle access is rejected.

Related test cases:

- TC-09
- TC-10
- TC-11
- TC-12

**Required Result:** Pass for core operations

---

# 4. Booking Evaluation

## EC-05 — Booking Can Be Created

The Customer must be able to complete the core booking workflow.

Required workflow:

`Vehicle → Service → Date → Time → Confirmation`

Success conditions:

- selected vehicle belongs to the customer;
- selected service is active;
- selected time is available;
- booking is stored;
- initial status is `Pending`.

Related test case:

- TC-16

**Required Result:** Pass

---

## EC-06 — Booking Conflicts Are Prevented

The system must prevent incompatible overlapping bookings.

Success conditions:

- occupied time is not offered as available;
- conflicting booking creation is rejected;
- conflicting records are not stored in the database.

Related test cases:

- TC-17
- TC-18
- TC-25

**Required Result:** Pass

This criterion is considered critical because preventing double booking is one of the main problems identified during user interviews.

---

## EC-07 — Booking Management Works

Customers must be able to manage eligible bookings.

Success conditions:

- customer can view own bookings;
- eligible booking can be cancelled;
- completed booking cannot be cancelled;
- eligible booking can be rescheduled to an available slot.

Related test cases:

- TC-21
- TC-22
- TC-23
- TC-24
- TC-25

**Required Result:** Core cases pass

---

# 5. Booking Status Evaluation

## EC-08 — Status Workflow Is Correct

The required booking workflow is:

`Pending → Confirmed → In Progress → Completed`

Alternative:

`Cancelled`

Success conditions:

- valid transitions are accepted;
- invalid transitions are rejected;
- updated status is stored correctly.

Related test cases:

- TC-26
- TC-27
- TC-28
- TC-29

**Required Result:** Pass

---

# 6. Mechanic Evaluation

## EC-09 — Mechanic Can Process Assigned Jobs

Success conditions:

- mechanic can view assigned jobs;
- mechanic can view daily jobs;
- confirmed job can be started;
- service can be completed;
- mechanic comment can be stored.

Related test cases:

- TC-27
- TC-28
- TC-30
- TC-31
- TC-32

**Required Result:** Main workflow passes

---

# 7. Administrator Evaluation

## EC-10 — Admin Can Manage Core Operations

Success conditions:

- Admin can view all bookings;
- Admin can confirm bookings;
- Admin can assign mechanics;
- Admin can manage services;
- Admin can access administrative functionality.

Related test cases:

- TC-08
- TC-14
- TC-33
- TC-34
- TC-35

**Required Result:** Pass for mandatory operations

---

# 8. Service History Evaluation

## EC-11 — Completed Services Are Stored in History

Success conditions:

- completed service appears under the correct vehicle;
- cancelled booking is not shown as completed history;
- service record remains associated with the correct customer and vehicle.

Related test cases:

- TC-36
- TC-37

**Required Result:** Pass

---

# 9. Security Evaluation

## EC-12 — Passwords Are Protected

Success conditions:

- passwords are not stored as plain text;
- password hashes are stored in the database.

Related test case:

- TC-38

**Required Result:** Pass

---

## EC-13 — Secrets Are Not Exposed

Success conditions:

- JWT secrets are not stored in tracked repository files;
- database passwords are not committed;
- environment-specific secrets are excluded.

Related test case:

- TC-41

**Required Result:** Pass

---

# 10. Reliability Evaluation

## EC-14 — Invalid Input Does Not Break the System

Success conditions:

- invalid requests return errors;
- backend remains available afterward;
- invalid operations do not corrupt data.

Related test cases:

- TC-44
- TC-45

**Required Result:** Pass for critical scenarios

---

# 11. Performance Evaluation

## EC-15 — Common Requests Respond Within Acceptable Time

Representative operations include:

- retrieving services;
- retrieving vehicles;
- retrieving bookings;
- retrieving available slots.

Target:

`≤ 2 seconds`

under expected development and demonstration conditions.

Related test cases:

- TC-42
- TC-43

**Required Result:** Should Pass

This is not treated as a strict production performance benchmark.

---

# 12. Usability Evaluation

## EC-16 — Core Customer Flow Is Understandable

The Customer should be able to complete:

`Login → Vehicle → Service → Date → Time → Confirmation`

Success conditions:

- navigation is understandable;
- required information is visible;
- error messages are understandable;
- user does not need unnecessary steps to complete the booking.

Related test cases:

- TC-46
- TC-47

**Required Result:** Should Pass

---

# 13. Critical Test Set for Pre-Defense

The following tests have the highest priority for the demonstration:

- TC-03 — Successful Login
- TC-05 — Protected Endpoint Without Token
- TC-06 — Customer Attempts Admin Operation
- TC-11 — Access Another Customer's Vehicle
- TC-16 — Successful Booking Creation
- TC-18 — Booking Conflict Prevention
- TC-26 — Confirm Pending Booking
- TC-27 — Start Confirmed Service
- TC-28 — Complete Service
- TC-29 — Invalid Status Transition
- TC-34 — Assign Mechanic
- TC-36 — Completed Service Appears in History
- TC-38 — Password Is Hashed
- TC-39 — Invalid JWT
- TC-44 — Invalid Request Does Not Crash Backend

All of these should pass before the final system demonstration.

---

# 14. Evaluation Levels

## Ready

The project is considered ready when:

- all critical test cases pass;
- the core booking workflow works;
- no critical security issue is identified;
- no blocking defect prevents demonstration.

---

## Partially Ready

The project is considered partially ready when:

- core functionality works;
- some non-critical Should Have functionality is incomplete;
- optional functionality is not implemented;
- no blocking defect affects the main workflow.

---

## Not Ready

The project is considered not ready when one or more critical issues exist, for example:

- users cannot authenticate;
- booking cannot be created;
- double booking is possible;
- roles are not protected;
- mechanic workflow cannot be completed;
- completed service does not reach service history;
- database consistency is broken.

---

# 15. Final Success Definition

The project will be considered successful when the complete main workflow can be demonstrated:

`Customer Registration/Login`

`↓`

`Vehicle Selection`

`↓`

`Service Selection`

`↓`

`Available Time Selection`

`↓`

`Booking Creation`

`↓`

`Admin Confirmation`

`↓`

`Mechanic Assignment`

`↓`

`Service In Progress`

`↓`

`Service Completed`

`↓`

`Vehicle Service History`

This end-to-end scenario represents the main objective of the proposed system.

---

# 16. Conclusion

The evaluation criteria provide a measurable definition of project success.

The highest priority is given to:

- authentication;
- authorization;
- booking correctness;
- conflict prevention;
- mechanic workflow;
- service history;
- security;
- data consistency.

Optional functions are useful extensions but are not required for successful verification of the core system.