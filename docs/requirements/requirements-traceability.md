# Requirements Traceability

## 1. Purpose

This document provides traceability between the main system requirements, user roles, evidence collected during the project, implementation priorities, and planned verification methods.

The goal is to ensure that mandatory requirements are:

- supported by project evidence;
- connected to a specific user need;
- assigned a priority;
- testable during implementation and final evaluation.

The primary evidence sources are:

- Project Proposal;
- User Interviews;
- Literature Review;
- Existing System Comparison;
- Technology Comparison.

---

# 2. Traceability Legend

## Requirement Types

- **FR** — Functional Requirement
- **NFR** — Non-Functional Requirement

## Priority

- **Must Have** — required for the core implementation
- **Should Have** — important, but can follow the core implementation
- **Could Have** — optional or future extension

## Evidence

- **Interview** — supported by user interviews
- **Literature** — supported by reviewed scientific literature
- **Existing Systems** — supported by comparison with existing automotive systems
- **Architecture** — required by the selected technical architecture
- **Project Scope** — defined as part of the approved project scope

---

# 3. Authentication and Access Control

## FR-01 — User Registration

**Role:** Customer  
**Priority:** Must Have

**Evidence:**

- Project Scope
- Architecture

**Reason:**

Customers require an account before vehicles, bookings, and service history can be associated with a specific user.

**Verification:**

Test registration with valid data and confirm that:

- a user record is created;
- the default role is Customer;
- duplicate email or phone data is rejected according to the registration rules.

---

## FR-02 — User Login

**Roles:** Customer, Mechanic, Admin  
**Priority:** Must Have

**Evidence:**

- Project Scope
- Architecture

**Verification:**

- valid credentials allow authentication;
- invalid credentials are rejected;
- successful authentication returns a valid JWT.

---

## FR-03 — Role-Based Access Control

**Roles:** Customer, Mechanic, Admin  
**Priority:** Must Have

**Evidence:**

- Literature Review
- Project Scope
- Technology Comparison

**Related source area:**

Research on role-based access control in web applications supports explicit backend authorization.

**Verification:**

Attempt protected actions using different roles.

Expected results:

- Customer cannot access Admin endpoints.
- Customer cannot access Mechanic-only operations.
- Mechanic cannot perform Admin operations.
- Admin can access authorized administrative operations.

---

# 4. Vehicle Management

## FR-04 — Add Vehicle

**Role:** Customer  
**Priority:** Must Have

**Evidence:**

- User Interviews
- Existing System Comparison
- Automotive-domain literature

**Reason:**

Vehicle information is required before a customer can create a service booking linked to a specific car.

**Verification:**

Create a vehicle and confirm that it is linked to the authenticated customer.

---

## FR-05 — View Own Vehicles

**Role:** Customer  
**Priority:** Must Have

**Evidence:**

- Project Scope
- Security requirements

**Verification:**

Confirm that a customer can view only vehicles associated with their own account.

---

## FR-06 — Edit Vehicle

**Role:** Customer  
**Priority:** Must Have

**Evidence:**

- Project Scope

**Verification:**

Update vehicle information and verify that unauthorized users cannot modify the vehicle.

---

# 5. Service Catalogue

## FR-08 — View Services

**Role:** Customer  
**Priority:** Must Have

**Evidence:**

- Car Owner Interview #1
- Car Owner Interview #2
- Mechanic Interview
- Administrator Interview
- Existing System Comparison

**Interview finding:**

Participants considered service descriptions, estimated duration, and price information useful before booking.

**Verification:**

Confirm that active services display:

- name;
- description;
- price;
- estimated duration.

---

## FR-09 — Manage Services

**Role:** Admin  
**Priority:** Must Have

**Evidence:**

- Administrator Interview
- Existing System Comparison
- Project Scope

**Verification:**

Confirm that Admin can:

- create;
- edit;
- activate;
- deactivate services.

Confirm that Customer and Mechanic users cannot perform these actions.

---

# 6. Booking Requirements

## FR-10 — Create Booking

**Role:** Customer  
**Priority:** Must Have

**Evidence:**

- All four user interviews
- Literature Review
- Existing System Comparison
- Project Proposal

**Reason:**

Online booking is the central business function of the proposed system.

**Verification:**

Create a booking using:

1. customer vehicle;
2. active service;
3. date;
4. available time slot.

Confirm that the booking is stored with status:

`Pending`

---

## FR-11 — Display Available Time Slots

**Role:** Customer  
**Priority:** Must Have

**Evidence:**

- All four user interviews
- Scheduling literature
- Existing System Comparison

**Interview finding:**

All four participants supported online visibility of available time slots.

**Verification:**

Create existing bookings and confirm that conflicting occupied periods are not displayed as available.

---

## FR-12 — Prevent Booking Conflicts

**Roles:** Customer, Admin  
**Priority:** Must Have

**Evidence:**

- Car Owner Interview #1
- Mechanic Interview
- Administrator Interview
- Literature Review
- Existing System Comparison

**Interview finding:**

Participants reported problems involving double bookings, overbooking, and incorrect service-duration planning.

**Verification:**

Attempt to create two incompatible bookings for the same limited resource and overlapping time interval.

Expected result:

The second conflicting booking is rejected.

---

## FR-13 — Customer Comment

**Role:** Customer  
**Priority:** Should Have

**Evidence:**

- Project Scope
- User Interview findings

**Verification:**

Create a booking with and without a comment.

Both operations should succeed.

---

# 7. Booking Management

## FR-14 — View My Bookings

**Role:** Customer  
**Priority:** Must Have

**Evidence:**

- Project Scope
- User Interviews

**Verification:**

Confirm that the authenticated customer sees only their own bookings.

---

## FR-16 — Cancel Booking

**Role:** Customer  
**Priority:** Must Have

**Evidence:**

- Car Owner Interview #1
- Literature Review

**Interview finding:**

The participant requested the ability to cancel an appointment when plans change.

**Verification:**

Cancel an eligible future booking.

Expected result:

`Status = Cancelled`

Completed bookings must not be cancellable.

---

## FR-17 — Reschedule Booking

**Role:** Customer  
**Priority:** Should Have

**Evidence:**

- Car Owner Interview #1
- Literature Review

**Verification:**

Attempt to reschedule an eligible booking to an available time.

Confirm that the new time is checked for conflicts before being accepted.

---

# 8. Status Management

## FR-18 — Booking Status Workflow

**Roles:** Mechanic, Admin  
**Priority:** Must Have

**Evidence:**

- All user interviews
- Existing System Comparison
- Project Scope

**Workflow:**

`Pending → Confirmed → In Progress → Completed`

Alternative:

`Cancelled`

**Verification:**

Test valid and invalid status transitions.

Invalid transitions must be rejected.

---

## FR-19 — Confirm Booking

**Role:** Admin  
**Priority:** Must Have

**Evidence:**

- Administrator Interview
- Project Scope

**Verification:**

Change a Pending booking to Confirmed and verify that the updated status is visible to relevant users.

---

# 9. Mechanic Requirements

## FR-20 — View Assigned Jobs

**Role:** Mechanic  
**Priority:** Must Have

**Evidence:**

- Mechanic Interview
- Existing System Comparison

**Interview finding:**

The mechanic currently receives work using printed schedules or verbal communication and identified a digital job list as useful.

**Verification:**

Assign a booking to a mechanic and confirm that it appears in that mechanic's job list.

---

## FR-21 — View Daily Jobs

**Role:** Mechanic  
**Priority:** Must Have

**Evidence:**

- Mechanic Interview

**Verification:**

Confirm that the mechanic can filter or view jobs scheduled for the working day.

---

## FR-22 — Start Service

**Role:** Mechanic  
**Priority:** Must Have

**Evidence:**

- Mechanic Interview
- Existing System Comparison

**Verification:**

Change an assigned job from:

`Confirmed → In Progress`

Confirm that the customer can observe the new status.

---

## FR-23 — Complete Service

**Role:** Mechanic  
**Priority:** Must Have

**Evidence:**

- Mechanic Interview
- Project Scope

**Verification:**

Change:

`In Progress → Completed`

Confirm that the completed booking becomes available in vehicle service history.

---

## FR-24 — Mechanic Comment

**Role:** Mechanic  
**Priority:** Should Have

**Evidence:**

- Mechanic Interview

**Verification:**

Add a mechanic comment to an authorized booking and confirm that it is stored correctly.

---

# 10. Service History

## FR-25 — Vehicle Service History

**Role:** Customer  
**Priority:** Must Have

**Evidence:**

- All four interviews
- Automotive Literature
- Existing System Comparison

**Interview finding:**

All participants considered digital vehicle service history useful.

**Verification:**

Complete a booking and confirm that:

- it appears under the correct vehicle;
- incomplete or cancelled bookings do not appear as completed service history;
- another customer cannot access the record.

---

## FR-26 — Mileage at Service

**Roles:** Mechanic, Admin  
**Priority:** Should Have

**Evidence:**

- Car owner interviews
- Automotive-domain requirements

**Verification:**

Store mileage when a service is completed and confirm that the value remains associated with the historical service record.

---

# 11. Administrator Requirements

## FR-27 — View All Bookings

**Role:** Admin  
**Priority:** Must Have

**Evidence:**

- Administrator Interview
- Existing System Comparison

**Verification:**

Admin can retrieve bookings across customers while normal Customer accounts cannot.

---

## FR-28 — Manage Bookings

**Role:** Admin  
**Priority:** Must Have

**Evidence:**

- Administrator Interview
- Project Scope

**Verification:**

Test allowed administrative booking actions and authorization restrictions.

---

## FR-29 — Assign Mechanic

**Role:** Admin  
**Priority:** Must Have

**Evidence:**

- Mechanic Interview
- Administrator Interview
- Existing System Comparison

**Verification:**

Assign a Mechanic user to a booking and verify that the job appears in the mechanic dashboard.

---

## FR-30 / FR-31 — User and Mechanic Management

**Role:** Admin  
**Priority:** Must Have

**Evidence:**

- Project Scope
- Existing System Comparison

**Verification:**

Confirm that administrative users can access user management functions while non-admin roles cannot.

---

## FR-32 — Daily Schedule

**Role:** Admin  
**Priority:** Must Have

**Evidence:**

- Administrator Interview
- Mechanic Interview

**Interview finding:**

The administrator currently checks spreadsheets and coordinates with mechanics to determine availability.

**Verification:**

Confirm that bookings for a selected date can be displayed in schedule order.

---

# 12. Optional Requirements

## FR-33 — Basic Statistics

**Role:** Admin  
**Priority:** Should Have

**Evidence:**

- Administrator Interview
- Existing System Comparison

**Verification:**

Compare displayed counts against database records.

---

## FR-34 — Appointment Reminders

**Priority:** Could Have

**Evidence:**

- Car Owner Interview #1
- Administrator Interview
- Literature Review

**Decision:**

Useful, but not mandatory for the first implementation.

---

## FR-35 — Multimedia Attachments

**Priority:** Could Have

**Evidence:**

- Car Owner Interview #2
- Mechanic Interview

**Decision:**

Optional extension after the core booking workflow is complete.

---

## FR-36 — Online Payment

**Priority:** Could Have / Out of Initial Scope

**Evidence:**

- Car Owner Interview #2
- Existing System Comparison

**Decision:**

Commercial platforms commonly provide online payments, but only one interview participant explicitly requested the feature.

Payment processing introduces additional external dependencies and security requirements.

Therefore, online payment is outside the initial implementation scope.

---

# 13. Non-Functional Requirement Traceability

## NFR-01 — Password Security

**Evidence:**

- Security best practice
- Authentication architecture

**Verification:**

Inspect database values and confirm passwords are stored only as hashes.

---

## NFR-03 — Role-Based Authorization

**Evidence:**

- Literature Review
- Project Architecture

**Verification:**

Perform API authorization tests for Customer, Mechanic, and Admin roles.

---

## NFR-04 — User Data Isolation

**Evidence:**

- Privacy and authorization requirements

**Verification:**

Attempt unauthorized access to another customer's vehicle or booking by changing resource identifiers.

Expected result:

`403 Forbidden` or equivalent authorization failure.

---

## NFR-06 — API Response Time

**Priority:** Should Have

**Verification:**

Measure representative endpoints under normal demonstration conditions.

Target:

Approximately **≤ 2 seconds** for common requests.

---

## NFR-09 — Booking Consistency

**Priority:** Must Have

**Verification:**

Simulate conflicting and invalid booking attempts.

Ensure failed requests do not produce incomplete booking records.

---

## NFR-12 / NFR-13 — Usability and Booking Flow

**Evidence:**

- User Interviews
- UX Prototype

**Verification:**

Test the full customer booking workflow:

`Vehicle → Service → Date → Time → Confirmation`

---

## NFR-18 — Version Control Traceability

**Evidence:**

- Diploma Git Repository Requirements

**Verification:**

Demonstrate:

- YouTrack issue;
- task branch;
- commits;
- Pull Request;
- merged changes.

---

# 14. Requirements by User Role

## Customer

Main mandatory functionality:

- registration;
- login;
- vehicle management;
- service catalogue;
- available slot viewing;
- booking creation;
- booking viewing;
- booking cancellation;
- status tracking;
- service history.

---

## Mechanic

Main mandatory functionality:

- login;
- assigned jobs;
- daily jobs;
- vehicle and service information;
- status updates;
- service completion.

---

## Administrator

Main mandatory functionality:

- login;
- service management;
- booking management;
- mechanic assignment;
- user and mechanic management;
- schedule management.

---

# 15. Priority Summary

## Must Have

Core implementation must include:

- Authentication
- Role authorization
- Vehicle management
- Service catalogue
- Available time slots
- Booking creation
- Booking conflict prevention
- Booking cancellation
- Booking status workflow
- Mechanic assigned jobs
- Admin booking management
- Service history

---

## Should Have

Important secondary functions:

- Vehicle deletion
- Customer booking comments
- Booking rescheduling
- Mechanic comments
- Mileage at service
- Basic dashboard statistics
- Responsive interface
- Docker deployment

---

## Could Have / Future Work

Optional extensions:

- Automated reminders
- SMS / WhatsApp integration
- Multimedia attachments
- Online payment
- Advanced analytics
- Inventory management
- Multi-location support

---

# 16. Conclusion

The traceability analysis demonstrates that the core requirements of the proposed system are not arbitrary.

They are derived from a combination of:

- verified user interview findings;
- academic literature;
- analysis of existing automotive systems;
- project scope;
- technical architecture.

Each mandatory requirement has a defined verification method, allowing its implementation to be demonstrated objectively during development, testing, and pre-defense.

This traceability will also be used as the basis for the project's verification and evaluation plan.