# Functional Requirements

## 1. Purpose

This document defines the functional requirements of the project **“Design and Development of a Web-Based Car Service Booking and Management System.”**

The requirements are based on:

- the approved project scope;
- user interviews with car owners, a mechanic, and a car service administrator;
- analysis of existing automotive workshop management systems;
- the selected system architecture and technology stack.

The system contains three user roles:

- Customer
- Mechanic
- Admin

Requirement priorities use the following classification:

- **Must Have** — required for the core system
- **Should Have** — important but may be implemented after core functionality
- **Could Have** — optional enhancement

---

# 2. Authentication and User Management

## FR-01 — User Registration

**Role:** Customer  
**Priority:** Must Have

The system shall allow a new customer to create an account using:

- name;
- email;
- phone number;
- password.

### Acceptance Criteria

- A user can submit valid registration data.
- Email addresses must be unique.
- Phone numbers must be unique.
- Passwords must not be stored as plain text.
- A successfully registered user receives a Customer role by default.

---

## FR-02 — User Login

**Roles:** Customer, Mechanic, Admin  
**Priority:** Must Have

The system shall allow registered users to authenticate using their credentials.

### Acceptance Criteria

- Valid credentials allow access to the system.
- Invalid credentials are rejected.
- A successful login returns an authentication token.
- The authenticated user's role is available to the backend authorization logic.

---

## FR-03 — Role-Based Access Control

**Roles:** Customer, Mechanic, Admin  
**Priority:** Must Have

The system shall restrict functionality according to the authenticated user's role.

### Acceptance Criteria

- Customers cannot access administrator functionality.
- Customers cannot access mechanic-only functionality.
- Mechanics cannot access administrator-only functionality.
- Administrative operations are accessible only to Admin users.
- Authorization is enforced on the backend, not only through the user interface.

---

# 3. Vehicle Management

## FR-04 — Add Vehicle

**Role:** Customer  
**Priority:** Must Have

The system shall allow a customer to register a vehicle.

The vehicle record shall include:

- brand;
- model;
- year;
- license plate;
- engine capacity;
- mileage.

### Acceptance Criteria

- A valid vehicle can be added.
- The vehicle is linked to the authenticated customer.
- The vehicle becomes visible in the customer's vehicle list.

---

## FR-05 — View Own Vehicles

**Role:** Customer  
**Priority:** Must Have

The system shall allow a customer to view all vehicles associated with their account.

### Acceptance Criteria

- Only vehicles belonging to the authenticated customer are displayed.
- Another customer's vehicles cannot be accessed.

---

## FR-06 — Edit Vehicle

**Role:** Customer  
**Priority:** Must Have

The system shall allow a customer to update information about their own vehicle.

### Acceptance Criteria

- The owner can modify allowed vehicle information.
- A customer cannot modify another user's vehicle.

---

## FR-07 — Delete Vehicle

**Role:** Customer  
**Priority:** Should Have

The system shall allow a customer to remove an eligible vehicle from their account.

### Acceptance Criteria

- Only the vehicle owner can request deletion.
- The system must preserve required historical data if the vehicle has completed service records.

---

# 4. Service Catalogue

## FR-08 — View Services

**Role:** Customer  
**Priority:** Must Have

The system shall display available car services.

Each service shall include:

- service name;
- description;
- price;
- estimated duration.

### Acceptance Criteria

- Active services are visible to customers.
- Service price and estimated duration are displayed before booking.

---

## FR-09 — Manage Services

**Role:** Admin  
**Priority:** Must Have

The administrator shall be able to create, edit, activate, deactivate, and manage car services.

### Acceptance Criteria

- Admin can create a service.
- Admin can change the service name, description, price, and duration.
- Inactive services cannot be selected for new bookings.
- Non-admin users cannot modify service configuration.

---

# 5. Appointment Booking

## FR-10 — Create Booking

**Role:** Customer  
**Priority:** Must Have

The system shall allow a customer to create a car service appointment.

The booking process shall include:

1. selecting a vehicle;
2. selecting a service;
3. selecting a date;
4. selecting an available time slot;
5. adding an optional comment;
6. confirming the booking.

### Acceptance Criteria

- The selected vehicle belongs to the authenticated customer.
- The selected service is active.
- The selected time slot is available.
- A booking is created with the status `Pending`.
- Booking information is stored in the database.

---

## FR-11 — Display Available Time Slots

**Role:** Customer  
**Priority:** Must Have

The system shall display available appointment times for the selected service and date.

### Acceptance Criteria

- Only available time slots are selectable.
- Existing bookings are considered when determining availability.
- Service duration is considered when determining availability.
- Conflicting appointments are not offered as available.

---

## FR-12 — Prevent Booking Conflicts

**Roles:** Customer, Admin  
**Priority:** Must Have

The system shall prevent incompatible overlapping bookings.

### Acceptance Criteria

- Before a booking is created, the backend validates availability.
- Two conflicting bookings cannot be successfully created for the same limited resource and time interval.

---

## FR-13 — Add Customer Comment

**Role:** Customer  
**Priority:** Should Have

The customer shall be able to add an optional comment to a booking.

Example:

`Please also check the brakes.`

### Acceptance Criteria

- A booking may be created without a comment.
- If provided, the comment is available to authorized service staff.

---

# 6. Customer Booking Management

## FR-14 — View My Bookings

**Role:** Customer  
**Priority:** Must Have

The customer shall be able to view their bookings.

### Acceptance Criteria

Each booking displays:

- vehicle;
- service;
- scheduled date and time;
- current status.

Only bookings belonging to the authenticated customer are displayed.

---

## FR-15 — View Booking Details

**Role:** Customer  
**Priority:** Must Have

The customer shall be able to open a booking and view detailed information.

### Acceptance Criteria

The booking detail includes relevant:

- vehicle information;
- service information;
- scheduled time;
- booking status;
- customer comment;
- mechanic information when assigned.

---

## FR-16 — Cancel Booking

**Role:** Customer  
**Priority:** Must Have

The customer shall be able to cancel an eligible future appointment.

### Acceptance Criteria

- A customer can cancel only their own booking.
- Completed bookings cannot be cancelled.
- Already cancelled bookings cannot be cancelled again.
- The booking status changes to `Cancelled`.

---

## FR-17 — Reschedule Booking

**Role:** Customer  
**Priority:** Should Have

The customer should be able to change the scheduled time of an eligible booking.

### Acceptance Criteria

- The customer can select only a new available slot.
- Conflict checks are performed before the appointment is updated.
- Completed and cancelled bookings cannot be rescheduled.

---

# 7. Booking Status Management

## FR-18 — Booking Status Workflow

**Roles:** Mechanic, Admin  
**Priority:** Must Have

The system shall support the following booking workflow:

`Pending → Confirmed → In Progress → Completed`

The system shall additionally support:

`Cancelled`

### Acceptance Criteria

- Booking statuses use the defined values.
- Invalid status transitions are rejected.
- Status changes are persisted in the database.

---

## FR-19 — Confirm Booking

**Role:** Admin  
**Priority:** Must Have

The administrator shall be able to confirm a pending booking.

### Acceptance Criteria

- A Pending booking may be changed to Confirmed.
- The updated status becomes visible to the customer.

---

# 8. Mechanic Functionality

## FR-20 — View Assigned Jobs

**Role:** Mechanic  
**Priority:** Must Have

The mechanic shall be able to view service jobs assigned to them.

### Acceptance Criteria

The mechanic can see:

- scheduled time;
- vehicle;
- service;
- customer comment;
- current status.

Mechanics do not see unrelated jobs unless explicitly permitted.

---

## FR-21 — View Daily Jobs

**Role:** Mechanic  
**Priority:** Must Have

The mechanic shall be able to view jobs scheduled for the current working day.

### Acceptance Criteria

- Jobs are displayed according to date.
- Relevant booking information is visible.

---

## FR-22 — Start Service

**Role:** Mechanic  
**Priority:** Must Have

A mechanic shall be able to change an assigned Confirmed booking to `In Progress`.

### Acceptance Criteria

- Only authorized staff can perform the operation.
- The new status is immediately stored.
- The customer can see the updated status.

---

## FR-23 — Complete Service

**Role:** Mechanic  
**Priority:** Must Have

A mechanic shall be able to mark an In Progress job as `Completed`.

### Acceptance Criteria

- Only an In Progress booking can normally be completed.
- Completion is stored in the database.
- The completed job becomes part of the vehicle's service history.

---

## FR-24 — Mechanic Comment

**Role:** Mechanic  
**Priority:** Should Have

The mechanic shall be able to add comments about performed work.

### Acceptance Criteria

- The mechanic can add or update an authorized service comment.
- The comment is associated with the correct booking.

---

# 9. Service History

## FR-25 — View Vehicle Service History

**Role:** Customer  
**Priority:** Must Have

The system shall allow customers to view completed service records for their vehicles.

### Acceptance Criteria

- Only completed services appear in service history.
- Records are linked to the correct vehicle.
- Customers cannot access the history of another user's vehicle.

---

## FR-26 — Record Mileage at Service

**Roles:** Mechanic, Admin  
**Priority:** Should Have

The system should record vehicle mileage associated with a completed service.

### Acceptance Criteria

- Mileage can be stored with the service record.
- Historical mileage remains associated with the completed booking.

---

# 10. Administrator Functionality

## FR-27 — View All Bookings

**Role:** Admin  
**Priority:** Must Have

The administrator shall be able to view all bookings in the system.

### Acceptance Criteria

Bookings can be viewed with relevant:

- customer;
- vehicle;
- service;
- mechanic;
- scheduled time;
- status.

---

## FR-28 — Manage Bookings

**Role:** Admin  
**Priority:** Must Have

The administrator shall be able to manage bookings when operational intervention is required.

### Acceptance Criteria

Admin can:

- view booking details;
- confirm bookings;
- cancel eligible bookings;
- manage assignment;
- update permitted booking information.

---

## FR-29 — Assign Mechanic

**Role:** Admin  
**Priority:** Must Have

The administrator shall be able to assign a mechanic to a booking.

### Acceptance Criteria

- Only users with the Mechanic role can be assigned.
- The assigned booking becomes visible in the mechanic's job list.

---

## FR-30 — Manage Users

**Role:** Admin  
**Priority:** Must Have

The administrator shall be able to view and manage system users.

### Acceptance Criteria

- Admin can view registered users.
- Administrative actions are protected by authorization.

---

## FR-31 — Manage Mechanics

**Role:** Admin  
**Priority:** Must Have

The administrator shall be able to manage users with the Mechanic role.

### Acceptance Criteria

- Admin can identify mechanic accounts.
- Mechanic accounts can be used for job assignment.

---

## FR-32 — View Daily Schedule

**Role:** Admin  
**Priority:** Must Have

The administrator shall be able to view the workshop schedule for a selected day.

### Acceptance Criteria

The schedule displays relevant bookings and times.

---

# 11. Dashboard and Statistics

## FR-33 — Admin Dashboard

**Role:** Admin  
**Priority:** Should Have

The system should provide basic operational statistics.

Possible statistics include:

- total bookings;
- completed bookings;
- pending bookings;
- active customers;
- bookings by status.

### Acceptance Criteria

- Statistics are generated from stored system data.
- Only authorized users can access the administrative dashboard.

---

# 12. Optional Extensions

## FR-34 — Appointment Reminders

**Priority:** Could Have

The system may support automated appointment reminders through an external communication service.

Possible channels:

- SMS;
- email;
- WhatsApp;
- push notifications.

This requirement is not mandatory for the first implementation.

---

## FR-35 — Multimedia Problem Description

**Priority:** Could Have

Customers may be allowed to attach photos, video, or audio describing a vehicle problem.

This function is considered a future extension and is not required for the core system.

---

## FR-36 — Online Payment

**Priority:** Could Have / Out of Initial Scope

The initial project will not require integrated online payment.

The feature may be considered in future work.

---

# 13. Functional Requirement Summary

The core Must Have requirements focus on the complete workflow:

`Registration`

`↓`

`Vehicle`

`↓`

`Service`

`↓`

`Available Time Slot`

`↓`

`Booking`

`↓`

`Confirmation`

`↓`

`Mechanic`

`↓`

`In Progress`

`↓`

`Completed`

`↓`

`Service History`

This workflow represents the minimum functional scope required for a successful implementation of the proposed system.