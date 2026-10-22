# Existing Systems Findings

## 1. Purpose

This document summarizes the main findings from the comparison of existing automotive workshop management systems and explains how these findings influence the scope and design of the proposed **Car Service Booking and Management System**.

The systems analyzed were:

- AutoLeap
- Tekmetric
- Shopmonkey
- Shop-Ware

---

## 2. Main Strengths of Existing Systems

The analyzed systems provide mature and comprehensive functionality for automotive workshop management.

Common strengths include:

- online appointment booking;
- customer and vehicle management;
- workshop scheduling;
- technician assignment;
- workflow and job-status tracking;
- service history;
- appointment reminders;
- reporting and analytics;
- payment functionality.

These systems demonstrate that centralized digital management of workshop operations is a well-established approach.

---

## 3. Main Limitations for the Purpose of This Diploma Project

The commercial systems provide significantly more functionality than is required for the proposed diploma project.

Examples of additional functionality found in commercial platforms include:

- inventory management;
- spare-parts ordering;
- payment processing;
- accounting integrations;
- customer relationship management;
- marketing automation;
- multi-location management;
- advanced reporting;
- advanced business analytics.

Implementing all of these features would create an unnecessarily large scope for a two-student diploma project.

Therefore, the proposed system intentionally focuses on the core booking and service-management workflow.

---

## 4. Features Confirmed as Important

The comparison confirms the relevance of several features already identified through user interviews.

### Online Booking

All selected systems support appointment scheduling.

**Project decision:**  
Online appointment booking remains a core requirement.

---

### Available Time Slots

Existing systems include scheduling and capacity-management functionality.

**Project decision:**  
Customers should only be able to select available time slots.

---

### Vehicle Management

All selected platforms maintain vehicle-related information.

**Project decision:**  
Customers should be able to register and manage multiple vehicles.

---

### Service History

Historical vehicle and repair information is commonly available.

**Project decision:**  
Completed services should be stored as part of the vehicle's service history.

---

### Mechanic Workflow

Existing platforms provide functionality for technicians or mechanics to work with assigned jobs.

**Project decision:**  
The Mechanic role will have a separate interface for assigned jobs and status updates.

---

### Status Tracking

Workflow stages are commonly used to manage service jobs.

**Project decision:**  
The proposed system will use:

`Pending → Confirmed → In Progress → Completed`

and additionally:

`Cancelled`

---

### Administrator Dashboard

Existing platforms provide centralized workshop management.

**Project decision:**  
The Admin role will manage bookings, services, users, mechanics, and schedules.

---

## 5. Features Excluded from the Initial Scope

Some features available in commercial products will not be included in the first version of the diploma project.

### Online Payments

Online payment functionality exists in commercial systems.

However, it introduces:

- external payment providers;
- additional security requirements;
- transaction handling;
- additional testing complexity.

**Decision:**  
Online payments remain outside the initial project scope.

---

### Inventory and Spare Parts

Commercial systems often provide parts and inventory management.

**Decision:**  
Inventory management is outside the scope because it is not required for the main booking workflow.

---

### Advanced Analytics

Commercial platforms provide detailed financial and operational analytics.

**Decision:**  
The proposed system will include only basic statistics, such as:

- total bookings;
- completed bookings;
- active customers;
- bookings by status.

---

### Marketing and CRM

Marketing campaigns, customer retention tools, and advanced CRM functionality are available in some commercial systems.

**Decision:**  
These functions are outside the diploma project scope.

---

### Multi-Location Management

Commercial systems may support multiple workshop branches.

**Decision:**  
The initial project will focus on a single car service organization.

---

## 6. Proposed System Position

The proposed project is not intended to compete directly with mature commercial products such as AutoLeap, Tekmetric, Shopmonkey, or Shop-Ware.

Instead, the project aims to design and implement a focused system that demonstrates the complete core workflow of a car service business.

The primary workflow is:

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

`Mechanic / Administrator Processing`

`↓`

`Completed Service`

`↓`

`Service History`

This workflow provides sufficient engineering complexity for a Software Engineering diploma project while keeping the implementation scope realistic.

---

## 7. Impact on Project Requirements

The comparison confirms the following main requirements:

- user authentication;
- Customer, Mechanic, and Admin roles;
- customer vehicle management;
- service catalogue;
- service price and duration;
- appointment booking;
- available time-slot selection;
- booking conflict prevention;
- booking cancellation;
- booking status tracking;
- mechanic job management;
- administrator scheduling;
- vehicle service history;
- basic operational statistics.

The following functions remain optional or future extensions:

- appointment reminders;
- appointment rescheduling;
- online payments;
- multimedia attachments;
- advanced analytics;
- inventory management;
- multi-location support.

---

## 8. Conclusion

The comparison of four existing automotive workshop management systems shows that the proposed functionality is consistent with real-world automotive service software.

The analysis also demonstrates that commercial platforms usually contain a much broader set of business functions than is necessary for this diploma project.

Therefore, the proposed system will focus on a smaller and clearly defined set of core functions that address the problems identified during the user interviews while remaining realistic for implementation by a two-student Software Engineering team.