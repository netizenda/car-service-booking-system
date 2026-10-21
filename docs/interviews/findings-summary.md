# Interview Findings Summary

## 1. Overview

Four user representatives were interviewed on 22 October 2026 to validate the initial assumptions behind the Car Service Booking and Management System.

The participants represented different perspectives:

- Car owner #1
- Car owner #2
- Mechanic
- Car service administrator

The interviews focused on the current appointment process, common problems, online time-slot selection, service information, booking status tracking, vehicle service history, and additional functionality.

---

## 2. Verified Findings

### Finding 1 — Current booking processes rely heavily on manual communication

Both car owners reported using phone calls or messaging applications to arrange appointments.

The mechanic stated that job information is communicated through printed schedules or verbal instructions.

The administrator reported using a combination of Excel spreadsheets, paper logbooks, WhatsApp messages, and phone calls.

**Conclusion:** Appointment and service information is currently distributed across several communication channels and tools.

**Resulting requirement:**  
The proposed system should provide a centralized web-based booking and appointment management process.

---

### Finding 2 — All participants considered online time-slot visibility useful

All four participants supported the ability to view available appointment times online.

Car owners emphasized convenience and avoiding repeated phone calls.

The mechanic highlighted better workload distribution.

The administrator indicated that self-service booking could reduce the number of customer calls.

**Resulting requirements:**

- Customers should be able to view available appointment dates and time slots.
- Unavailable time slots should not be selectable.
- Booking availability should consider the expected duration of the selected service.
- The system should prevent conflicting bookings.

---

### Finding 3 — Scheduling conflicts and overbooking are important problems

Car owner #1 reported experiencing overlapping appointments.

The mechanic identified overbooking and incorrect service-duration estimates as major causes of delays.

The administrator also reported occasional double bookings caused by human error.

**Resulting requirements:**

- The system should prevent conflicting appointments.
- Each service should contain an estimated duration.
- Booking availability should be calculated using the selected service duration.
- Administrators should have an overview of the daily schedule.

---

### Finding 4 — All participants considered service information important

All four participants supported displaying service descriptions and estimated duration.

Both car owners emphasized the importance of seeing prices before booking.

The mechanic stated that standardized service descriptions and duration estimates improve planning.

The administrator stated that predefined service packages could reduce misunderstandings.

**Resulting requirements:**

Each service should contain:

- service name;
- description;
- estimated price;
- estimated duration;
- availability status.

Customers should be able to view this information before creating a booking.

---

### Finding 5 — All participants supported booking status tracking

All four participants considered service status tracking useful.

Customers want to know whether their vehicle is still waiting, currently being serviced, or ready for pickup.

The mechanic indicated that changing the job status digitally could immediately communicate progress to both the administrator and customer.

The administrator stated that statuses would help monitor workflow.

**Resulting requirement:**

The system should support the following booking status workflow:

Pending → Confirmed → In Progress → Completed

The system should additionally support:

Cancelled

---

### Finding 6 — Vehicle service history was considered useful by all participants

Both car owners stated that digital service history would help them remember previous maintenance and avoid losing paper records.

The mechanic stated that previous repair information could help with future diagnostics.

The administrator stated that service history could improve support for returning customers.

**Resulting requirements:**

- Completed services should be stored in vehicle service history.
- Service history should be linked to a specific vehicle.
- Each completed record should contain the service date.
- The system should store vehicle mileage at the time of service.
- The system should store information about the performed service.

---

### Finding 7 — Mechanics need their own job-management interface

The mechanic reported currently receiving information through printed schedules and verbal communication.

The participant considered a digital job list and direct status updates useful.

**Resulting requirements:**

The Mechanic role should be able to:

- view assigned jobs;
- view vehicle information;
- view selected services;
- view customer comments;
- change job status;
- add mechanic comments.

---

### Finding 8 — Administrators need centralized schedule management

The administrator currently combines spreadsheets, paper records, calls, and messages.

The participant identified double bookings, high call volume, and no-shows as important operational problems.

**Resulting requirements:**

The Administrator role should be able to:

- view all bookings;
- view the daily schedule;
- manage bookings;
- manage services;
- manage service prices and durations;
- manage users and mechanics;
- assign mechanics to bookings;
- view basic operational statistics.

---

## 3. Additional Feature Requests

Participants also suggested several additional functions.

### Appointment reminders

Suggested by:

- Car owner #1
- Car service administrator

Possible functionality:

- appointment reminders;
- completed-service notifications.

**Decision:** Useful enhancement. It may be included if development time allows.

---

### Rescheduling appointments

Suggested by Car owner #1.

**Decision:** This should be considered for the main booking functionality because it directly relates to appointment management.

---

### Online payments or deposits

Suggested by Car owner #2.

Only one participant explicitly requested this functionality.

**Decision:** Online payment will remain outside the initial project scope and may be considered as future work.

---

### Photo, video, and audio attachments

Car owner #2 suggested uploading media describing vehicle problems.

The mechanic suggested attaching photos of damaged or worn components to a job.

**Decision:** Useful functionality, but not required for the first implementation. It may be considered as an extension if the core system is completed.

---

### Reporting and analytics

The administrator suggested statistics such as:

- daily revenue;
- lift utilization;
- most requested services.

**Decision:** The initial system will include only basic statistics. More advanced business analytics can be considered future work.

---

## 4. Requirements Confirmed by Interview Evidence

Based on the four interviews, the following previously proposed features received direct support:

| Requirement | Evidence |
|---|---|
| Online appointment booking | Supported by all participants |
| Available time-slot selection | Supported by all participants |
| Service descriptions | Supported by all participants |
| Service prices | Supported by customer and administrator interviews |
| Estimated service duration | Supported by all participants |
| Booking status tracking | Supported by all participants |
| Vehicle service history | Supported by all participants |
| Mechanic dashboard | Supported by mechanic interview |
| Admin scheduling dashboard | Supported by administrator interview |
| Booking conflict prevention | Supported by customer, mechanic, and administrator interviews |
| Booking cancellation | Supported by customer interview |
| Appointment rescheduling | Supported by customer interview |

---

## 5. Initial Assumptions and Interview Results

### Assumption: Customers need online booking

**Result:** Supported.

Both interviewed car owners considered online booking and visible time slots useful.

---

### Assumption: Customers need booking status tracking

**Result:** Supported.

All four participants considered status tracking useful.

---

### Assumption: Vehicle service history is useful

**Result:** Supported.

All participants considered vehicle service history valuable.

---

### Assumption: Mechanics require a separate interface

**Result:** Supported.

The mechanic described the need for assigned-job information and direct status updates.

---

### Assumption: Administrators require centralized scheduling

**Result:** Supported.

The administrator described difficulties caused by managing appointments across spreadsheets, paper records, calls, and messages.

---

### Assumption: Online payment is necessary for the first version

**Result:** Not sufficiently supported.

Only one participant explicitly requested online payment.

**Decision:** Keep online payment outside the initial project scope.

---

## 6. Impact on Project Scope

The interviews support the core functionality originally proposed for the project.

The following functions remain part of the initial scope:

- user authentication;
- Customer, Mechanic, and Admin roles;
- vehicle management;
- service catalogue;
- service prices and estimated duration;
- appointment booking;
- available time-slot selection;
- booking conflict prevention;
- booking cancellation;
- booking status management;
- vehicle service history;
- mechanic dashboard;
- administrator dashboard;
- basic statistics.

The following functions are currently considered optional or future extensions:

- online payments;
- advanced analytics;
- photo/video/audio attachments;
- external WhatsApp or SMS integration;
- push notifications.

---

## 7. Conclusion

The interviews provided evidence that the proposed system addresses problems experienced by different participants in the car service process.

The strongest recurring findings were related to manual appointment management, lack of visible appointment availability, scheduling conflicts, limited service information, repeated status inquiries, and fragmented vehicle service history.

The interview results therefore support the core requirements of the proposed Car Service Booking and Management System while also identifying several optional features that can be considered after implementation of the core functionality.