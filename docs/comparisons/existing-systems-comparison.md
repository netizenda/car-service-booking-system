# Existing Systems Comparison

## 1. Purpose

This document compares four existing automotive workshop management systems with the proposed **Car Service Booking and Management System**.

The selected systems are:

- AutoLeap
- Tekmetric
- Shopmonkey
- Shop-Ware

The comparison uses the same functional criteria for all systems.

---

## 2. Comparison Criteria

The systems are compared using the following ten criteria:

1. Online appointment booking
2. Time-slot and capacity management
3. Customer and vehicle management
4. Vehicle/service history
5. Mechanic or technician workflow
6. Job or booking status tracking
7. Appointment reminders and customer communication
8. Role and permission management
9. Reporting and analytics
10. Online payments

---

# 3. Online Appointment Booking

### AutoLeap
Supports online appointment booking for customers.

### Tekmetric
Supports online scheduling and customer appointment requests.

### Shopmonkey
Provides an online appointment scheduler.

### Shop-Ware
Supports online service scheduling.

### Proposed System
**Planned.**

Customers will be able to select a vehicle, service, date, and available time slot online.

**Conclusion:**  
Online booking is a common feature across all analyzed systems and is therefore an important requirement for the proposed project.

---

# 4. Time-Slot and Capacity Management

### AutoLeap
Supports scheduling based on workshop and technician availability.

### Tekmetric
Provides configurable shop availability and scheduling controls to reduce overbooking.

### Shopmonkey
Supports configurable service durations and appointment scheduling.

### Shop-Ware
Provides real-time availability and capacity-aware scheduling.

### Proposed System
**Planned.**

Available time slots will depend on:

- selected service;
- estimated service duration;
- schedule availability.

The system should prevent conflicting bookings.

**Conclusion:**  
Existing systems demonstrate that booking availability should reflect actual workshop capacity rather than allowing customers to choose any arbitrary time.

---

# 5. Customer and Vehicle Management

### AutoLeap
Stores customer and vehicle information.

### Tekmetric
Maintains customer profiles, notes, and vehicle information.

### Shopmonkey
Includes customer and vehicle records.

### Shop-Ware
Supports customer and vehicle information as part of repair-order management.

### Proposed System
**Planned.**

Customers will be able to register multiple vehicles containing:

- brand;
- model;
- year;
- license plate;
- engine information;
- mileage.

**Conclusion:**  
Vehicle profiles are a standard component of automotive workshop management systems and are necessary for connecting bookings and service history to a specific vehicle.

---

# 6. Vehicle and Service History

### AutoLeap
Provides access to customer and vehicle service history.

### Tekmetric
Maintains customer and repair history.

### Shopmonkey
Provides vehicle and work-order history functionality.

### Shop-Ware
Maintains historical repair and vehicle information.

### Proposed System
**Planned.**

Completed bookings will form a service history for each customer vehicle.

The history should include:

- service performed;
- service date;
- vehicle mileage;
- mechanic comments;
- booking status.

**Conclusion:**  
Digital service history is supported by existing systems and was also requested during the project's user interviews.

---

# 7. Mechanic / Technician Workflow

### AutoLeap
Provides technician-oriented workflow and job assignment functionality.

### Tekmetric
Supports repair-order and technician workflow management.

### Shopmonkey
Provides technician assignment and a technician mobile application.

### Shop-Ware
Provides a dedicated technician workflow and job interface.

### Proposed System
**Planned.**

Mechanics will be able to:

- view assigned jobs;
- view vehicle information;
- view selected service;
- view customer comments;
- update job status;
- add mechanic comments.

**Conclusion:**  
A separate mechanic workflow is common in professional workshop management systems and supports clearer internal task management.

---

# 8. Job and Booking Status Tracking

### AutoLeap
Supports job and workflow tracking.

### Tekmetric
Tracks repair orders through workshop workflows.

### Shopmonkey
Supports workflow stages for jobs and work orders.

### Shop-Ware
Supports configurable repair-order statuses and workflow stages.

### Proposed System
**Planned.**

The main workflow will be:

`Pending → Confirmed → In Progress → Completed`

The system will also support:

`Cancelled`

**Conclusion:**  
Status-based workflow is a common method for organizing automotive service jobs and will be included in the proposed system.

---

# 9. Appointment Reminders and Customer Communication

### AutoLeap
Supports automated reminders and customer communication.

### Tekmetric
Provides appointment reminders and customer messaging functionality.

### Shopmonkey
Supports appointment confirmations and reminders.

### Shop-Ware
Includes customer communication and reminder functionality.

### Proposed System
**Optional / Planned Extension.**

The core system will support booking information and status tracking.

Automated SMS, WhatsApp, email, or push notifications may be implemented if development time allows.

**Conclusion:**  
Reminder functionality is useful but is not required for the initial minimum viable implementation.

---

# 10. Role and Permission Management

### AutoLeap
Provides employee access and management functionality.

### Tekmetric
Provides configurable employee roles and permissions.

### Shopmonkey
Supports different staff access levels and workflow responsibilities.

### Shop-Ware
Separates technician and management functionality within workshop workflows.

### Proposed System
**Planned.**

Three roles will be implemented:

- Customer
- Mechanic
- Admin

Permissions will be enforced by the backend using JWT authentication and role-based authorization.

**Conclusion:**  
Role separation is necessary because different user groups require different system actions and access levels.

---

# 11. Reporting and Analytics

### AutoLeap
Provides business reporting and analytics.

### Tekmetric
Includes reporting and shop performance analytics.

### Shopmonkey
Provides workshop reporting and business insights.

### Shop-Ware
Includes reporting and analytics functionality.

### Proposed System
**Basic functionality planned.**

The initial version may include statistics such as:

- total bookings;
- completed bookings;
- active customers;
- bookings by status.

Advanced business analytics are outside the initial project scope.

**Conclusion:**  
Commercial systems provide extensive analytics, while the proposed diploma project will intentionally limit this feature to basic operational statistics.

---

# 12. Online Payments

### AutoLeap
Supports payment functionality.

### Tekmetric
Provides integrated payment functionality.

### Shopmonkey
Supports payment processing.

### Shop-Ware
Provides digital payment functionality.

### Proposed System
**Out of scope.**

Online payment was suggested by one interview participant but was not identified as a core requirement.

Payment integration would also introduce additional external dependencies and security requirements.

**Conclusion:**  
Online payments are valuable in commercial products but are not required to demonstrate the primary booking and workshop-management workflow of the diploma project.

---

# 13. Overall Comparison

The analyzed commercial systems contain significantly broader functionality than the proposed diploma project.

Common commercial capabilities include:

- inventory management;
- parts ordering;
- payment processing;
- marketing tools;
- advanced analytics;
- accounting integrations;
- multi-location management;
- customer relationship management.

The proposed system intentionally focuses on a smaller set of core functions:

`Customer`

`↓`

`Vehicle`

`↓`

`Service`

`↓`

`Available Time Slot`

`↓`

`Booking`

`↓`

`Mechanic Processing`

`↓`

`Completed Service`

`↓`

`Service History`

This scope is more appropriate for a two-student Software Engineering diploma project while still demonstrating frontend development, backend development, database design, authorization, REST API integration, scheduling logic, and testing.

---

# 14. Main Findings

The comparison leads to the following findings:

1. Online booking is a standard capability in modern automotive workshop systems.

2. Booking availability should consider actual workshop capacity and service duration.

3. Customer and vehicle records are fundamental for connecting appointments with service history.

4. Mechanic workflows and job-status tracking are important for internal workshop operations.

5. Customer reminders and communication are useful but can remain optional in the first implementation.

6. Commercial systems often include advanced payments, inventory, marketing, and analytics features that are not necessary for the initial diploma scope.

7. The proposed system does not attempt to replace existing commercial platforms.

8. The project instead aims to implement and demonstrate the core end-to-end automotive service workflow within a realistic academic scope.

---

# 15. Conclusion

The comparison of AutoLeap, Tekmetric, Shopmonkey, and Shop-Ware confirms that the functional areas selected for the proposed project are relevant to real automotive service management systems.

The existing systems demonstrate the practical importance of online scheduling, vehicle records, technician workflows, service history, booking-status tracking, and centralized administration.

At the same time, commercial platforms typically include a much wider range of business functionality.

Therefore, the proposed Car Service Booking and Management System will focus on a clearly defined subset of functionality that is sufficient to address the problems identified during user interviews and to demonstrate the required software engineering complexity of the diploma project.