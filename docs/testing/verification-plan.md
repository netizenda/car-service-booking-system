# Verification and Evaluation Plan

## 1. Purpose

This document defines the verification and evaluation approach for the project **“Design and Development of a Web-Based Car Service Booking and Management System.”**

The purpose of verification is to confirm that the implemented system satisfies the defined functional and non-functional requirements.

The evaluation will focus on:

- functional correctness;
- role-based access control;
- booking workflow correctness;
- data integrity;
- usability of the main user flows;
- API behavior;
- basic security;
- performance under expected demonstration conditions.

---

# 2. Verification Strategy

The project will use several verification methods:

- Functional testing
- API testing
- Role-based access testing
- Negative testing
- Database verification
- Manual UI testing
- Performance checks
- Security checks

The main tools may include:

- Postman
- Web browser
- PostgreSQL database tools
- Backend logs
- GitHub
- Manual test scenarios

---

# 3. Functional Verification

## Authentication

The following functions will be tested:

- user registration;
- login;
- invalid login;
- duplicate registration;
- protected endpoint access.

Expected result:

Only valid users should be authenticated and protected operations should reject unauthorized requests.

---

## Role-Based Access Control

The following roles will be tested:

- Customer
- Mechanic
- Admin

Expected result:

Each role should only access functionality allowed by the system requirements.

Examples:

- Customer cannot access admin endpoints.
- Customer cannot access mechanic-only endpoints.
- Mechanic cannot perform admin operations.
- Admin can access administrative functionality.

---

## Vehicle Management

The following functions will be tested:

- add vehicle;
- view own vehicles;
- edit vehicle;
- delete eligible vehicle;
- unauthorized vehicle access.

Expected result:

Customers should only manage vehicles associated with their own accounts.

---

## Service Catalogue

The following functions will be tested:

- view active services;
- service price display;
- service duration display;
- admin service creation;
- admin service editing;
- service activation and deactivation.

Expected result:

Customers should only see active services and only Admin users should be able to manage service configuration.

---

# 4. Booking Verification

## Create Booking

Test flow:

1. Login as Customer.
2. Select a vehicle.
3. Select a service.
4. Select a date.
5. Select an available time slot.
6. Add an optional comment.
7. Confirm booking.

Expected result:

A new booking should be created with status:

`Pending`

---

## Available Time Slots

Test scenario:

Create existing bookings for selected times.

Expected result:

Occupied or conflicting times should not be displayed as available.

---

## Booking Conflict Prevention

Test scenario:

Attempt to create two incompatible bookings for the same limited resource and overlapping time interval.

Expected result:

The second conflicting booking must be rejected.

No duplicate or inconsistent booking should be stored.

---

## Booking Cancellation

Test scenario:

Cancel an eligible future booking.

Expected result:

The booking status becomes:

`Cancelled`

Completed bookings should not be cancellable.

---

## Booking Rescheduling

Test scenario:

Move an eligible booking to another available time slot.

Expected result:

The new time is accepted only if it does not conflict with another booking.

---

# 5. Booking Status Workflow

The following status workflow will be verified:

`Pending → Confirmed → In Progress → Completed`

Alternative final state:

`Cancelled`

Tests will confirm:

- valid status transitions are accepted;
- invalid transitions are rejected;
- status changes are stored correctly;
- updated status becomes visible to relevant users.

---

# 6. Mechanic Workflow Verification

The following mechanic functions will be tested:

- login;
- view assigned jobs;
- view daily jobs;
- view vehicle and service details;
- start service;
- add mechanic comment;
- complete service.

Expected result:

The mechanic should only work with authorized assigned jobs.

After completion, the service should become part of the vehicle service history.

---

# 7. Admin Workflow Verification

The following admin functions will be tested:

- view all bookings;
- confirm bookings;
- assign mechanics;
- manage services;
- manage users;
- manage mechanics;
- view workshop schedule;
- view basic statistics.

Expected result:

Administrative functionality should only be available to Admin users.

---

# 8. Service History Verification

Test scenario:

Complete a service booking.

Expected result:

The completed booking should appear in the service history of the correct vehicle.

The record should contain relevant information such as:

- service;
- date;
- vehicle;
- mileage, when available;
- completion status.

Cancelled or incomplete bookings should not appear as completed service history.

---

# 9. API Verification

The REST API will be tested using Postman.

Tests will include:

- valid requests;
- invalid requests;
- missing authentication;
- invalid authentication token;
- incorrect resource identifiers;
- invalid request body;
- role authorization.

Expected HTTP response codes may include:

- `200 OK`
- `201 Created`
- `400 Bad Request`
- `401 Unauthorized`
- `403 Forbidden`
- `404 Not Found`
- `409 Conflict`
- `500 Internal Server Error`

The exact response code will depend on the endpoint and scenario.

---

# 10. Negative Testing

Negative tests will verify that the system correctly rejects invalid behavior.

Examples:

- login with incorrect password;
- register with duplicate email;
- access another customer's vehicle;
- access another customer's booking;
- create booking using an invalid vehicle;
- create booking using inactive service;
- book an unavailable time slot;
- perform invalid booking status transition;
- access Admin endpoint as Customer;
- access Mechanic endpoint as Customer.

Expected result:

Invalid operations are rejected without corrupting application data.

---

# 11. Security Verification

Basic security verification will include:

## Password Storage

Verify that passwords are stored as hashes rather than plain text.

## JWT Protection

Verify that protected endpoints reject:

- missing token;
- invalid token;
- expired token.

## Role Authorization

Verify that backend authorization checks prevent access based on role.

## Data Isolation

Verify that customers cannot access another customer's private resources.

## Secret Management

Verify that real secrets are not committed to the GitHub repository.

---

# 12. Non-Functional Verification

## Performance

Representative API endpoints will be measured under normal demonstration conditions.

Target:

Common requests should normally complete within approximately:

`≤ 2 seconds`

Example endpoints:

- services;
- vehicles;
- bookings;
- mechanic daily jobs.

---

## Usability

The main Customer workflow will be manually evaluated:

`Login → Vehicle → Service → Date → Time → Confirmation`

Evaluation questions:

- Is the next action clear?
- Is required information visible?
- Are errors understandable?
- Can the user complete the workflow without unnecessary steps?

---

## Reliability

Verification will confirm that:

- invalid requests do not crash the backend;
- database errors are handled;
- failed booking attempts do not create incomplete records;
- booking state remains consistent.

---

# 13. Evaluation Criteria

The implementation will be considered successful when:

- core Must Have requirements are implemented;
- mandatory test cases pass;
- role-based access works correctly;
- booking conflicts are prevented;
- the complete booking workflow works;
- mechanics can process assigned jobs;
- Admin can manage core operational data;
- completed services appear in service history;
- major security checks pass;
- no critical defects prevent demonstration of the core workflow.

---

# 14. Evaluation Priorities

## Critical

- Authentication
- Authorization
- Booking creation
- Booking conflict prevention
- Booking status workflow
- Data isolation
- Database consistency

## High

- Vehicle management
- Service management
- Mechanic workflow
- Admin workflow
- Service history

## Medium

- Rescheduling
- Dashboard statistics
- Responsive layout
- Docker environment

## Optional

- Automated reminders
- Multimedia attachments
- Online payments
- Advanced analytics

---

# 15. Verification Evidence

Evidence collected during testing may include:

- Postman screenshots;
- API responses;
- browser screenshots;
- database records;
- test results;
- backend logs;
- GitHub commits;
- documented defects and fixes.

---

# 16. Conclusion

The verification and evaluation plan provides a structured method for confirming that the developed system satisfies the defined requirements.

The plan focuses primarily on the complete booking lifecycle:

`Customer → Booking → Admin Confirmation → Mechanic Service → Completion → Service History`

This workflow represents the core value of the proposed system and will receive the highest verification priority.