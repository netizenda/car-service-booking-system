# Test Cases

## 1. Purpose

This document defines the initial test cases for the project **“Design and Development of a Web-Based Car Service Booking and Management System.”**

Each test case includes:

- Test Case ID
- Related Requirement
- Test Scenario
- Preconditions
- Test Steps
- Expected Result
- Priority

---

# 2. Authentication Test Cases

## TC-01 — Successful User Registration

**Related Requirement:** FR-01  
**Priority:** Critical

**Preconditions:**

- User is not registered.
- Email and phone number are unique.

**Test Steps:**

1. Open the registration page.
2. Enter a valid name.
3. Enter a unique email.
4. Enter a unique phone number.
5. Enter a valid password.
6. Submit the form.

**Expected Result:**

- Registration succeeds.
- User account is created.
- Default role is Customer.
- Password is stored as a hash.

---

## TC-02 — Duplicate Email Registration

**Related Requirements:** FR-01, NFR-22  
**Priority:** High

**Preconditions:**

- A user with the selected email already exists.

**Test Steps:**

1. Open the registration page.
2. Enter an existing email.
3. Enter other valid registration data.
4. Submit the form.

**Expected Result:**

- Registration is rejected.
- No duplicate account is created.
- User receives an understandable error message.

---

## TC-03 — Successful Login

**Related Requirement:** FR-02  
**Priority:** Critical

**Preconditions:**

- User account exists.

**Test Steps:**

1. Open the login page.
2. Enter valid credentials.
3. Submit the form.

**Expected Result:**

- Authentication succeeds.
- User receives a valid authentication token.
- User is redirected to the appropriate interface.

---

## TC-04 — Invalid Login

**Related Requirement:** FR-02  
**Priority:** Critical

**Test Steps:**

1. Enter a valid email.
2. Enter an incorrect password.
3. Submit the login form.

**Expected Result:**

- Authentication fails.
- Access is denied.
- No valid JWT is issued.

---

## TC-05 — Protected Endpoint Without Token

**Related Requirements:** NFR-02, FR-03  
**Priority:** Critical

**Test Steps:**

1. Send a request to a protected endpoint without an authentication token.

**Expected Result:**

- Request is rejected.
- Response is `401 Unauthorized` or equivalent.

---

# 3. Role-Based Access Test Cases

## TC-06 — Customer Attempts Admin Operation

**Related Requirements:** FR-03, NFR-03  
**Priority:** Critical

**Preconditions:**

- User is authenticated as Customer.

**Test Steps:**

1. Attempt to access an Admin endpoint.
2. Attempt to modify service configuration.

**Expected Result:**

- Operation is rejected.
- Customer does not receive Admin permissions.
- Response is `403 Forbidden` or equivalent.

---

## TC-07 — Customer Attempts Mechanic Operation

**Related Requirements:** FR-03, NFR-03  
**Priority:** Critical

**Preconditions:**

- User is authenticated as Customer.

**Test Steps:**

1. Attempt to change a booking status to `In Progress`.

**Expected Result:**

- Operation is rejected.

---

## TC-08 — Admin Accesses Administrative Functionality

**Related Requirement:** FR-03  
**Priority:** High

**Preconditions:**

- User is authenticated as Admin.

**Test Steps:**

1. Open the Admin dashboard.
2. Open booking management.
3. Open service management.

**Expected Result:**

- Admin can access all authorized administrative functionality.

---

# 4. Vehicle Management Test Cases

## TC-09 — Add Vehicle

**Related Requirement:** FR-04  
**Priority:** High

**Preconditions:**

- Customer is authenticated.

**Test Steps:**

1. Open `My Cars`.
2. Select `Add Vehicle`.
3. Enter valid vehicle information.
4. Save the vehicle.

**Expected Result:**

- Vehicle is created.
- Vehicle is linked to the authenticated customer.
- Vehicle appears in `My Cars`.

---

## TC-10 — View Own Vehicles

**Related Requirement:** FR-05  
**Priority:** High

**Preconditions:**

- Customer owns at least one vehicle.

**Test Steps:**

1. Login as Customer.
2. Open `My Cars`.

**Expected Result:**

- Customer sees their own vehicles.

---

## TC-11 — Access Another Customer's Vehicle

**Related Requirements:** FR-05, NFR-04  
**Priority:** Critical

**Preconditions:**

- Two Customer accounts exist.
- Customer A owns Vehicle A.

**Test Steps:**

1. Login as Customer B.
2. Attempt to request Vehicle A using its ID.

**Expected Result:**

- Access is rejected.
- Vehicle information is not exposed.

---

## TC-12 — Edit Own Vehicle

**Related Requirement:** FR-06  
**Priority:** High

**Test Steps:**

1. Login as Customer.
2. Open one of the customer's vehicles.
3. Change mileage or another editable field.
4. Save changes.

**Expected Result:**

- Vehicle information is updated successfully.

---

# 5. Service Catalogue Test Cases

## TC-13 — View Active Services

**Related Requirement:** FR-08  
**Priority:** High

**Test Steps:**

1. Open the Services page.

**Expected Result:**

Active services display:

- name;
- description;
- price;
- estimated duration.

---

## TC-14 — Admin Creates Service

**Related Requirement:** FR-09  
**Priority:** High

**Preconditions:**

- Admin is authenticated.

**Test Steps:**

1. Open Service Management.
2. Select `Create Service`.
3. Enter name, description, price, and duration.
4. Save.

**Expected Result:**

- New service is stored successfully.
- New active service becomes available to customers.

---

## TC-15 — Customer Attempts Service Modification

**Related Requirements:** FR-09, NFR-03  
**Priority:** Critical

**Preconditions:**

- Customer is authenticated.

**Test Steps:**

1. Attempt to call the service modification endpoint.

**Expected Result:**

- Request is rejected.

---

# 6. Booking Test Cases

## TC-16 — Successful Booking Creation

**Related Requirement:** FR-10  
**Priority:** Critical

**Preconditions:**

- Customer is authenticated.
- Customer has a vehicle.
- Active service exists.
- Available time slot exists.

**Test Steps:**

1. Select vehicle.
2. Select service.
3. Select date.
4. Select available time slot.
5. Add optional comment.
6. Confirm booking.

**Expected Result:**

- Booking is created.
- Booking status is `Pending`.
- Correct customer, vehicle, service, date, and time are stored.

---

## TC-17 — Available Time Slots

**Related Requirement:** FR-11  
**Priority:** Critical

**Preconditions:**

- Some time slots already contain bookings.

**Test Steps:**

1. Select service.
2. Select date.
3. Request available time slots.

**Expected Result:**

- Available slots are displayed.
- Conflicting occupied time slots are not selectable.

---

## TC-18 — Booking Conflict Prevention

**Related Requirements:** FR-12, NFR-09  
**Priority:** Critical

**Preconditions:**

- Booking exists for a limited resource at 14:00.

**Test Steps:**

1. Attempt to create another incompatible booking for an overlapping period.

**Expected Result:**

- New booking is rejected.
- Existing booking remains unchanged.
- No conflicting database record is created.

---

## TC-19 — Booking With Invalid Vehicle

**Related Requirement:** FR-10  
**Priority:** Critical

**Preconditions:**

- Customer is authenticated.

**Test Steps:**

1. Attempt to create a booking using a vehicle ID belonging to another customer.

**Expected Result:**

- Booking is rejected.

---

## TC-20 — Booking With Inactive Service

**Related Requirements:** FR-09, FR-10  
**Priority:** High

**Preconditions:**

- Service exists but is inactive.

**Test Steps:**

1. Attempt to create a booking using the inactive service.

**Expected Result:**

- Booking is rejected.

---

# 7. Booking Management Test Cases

## TC-21 — View Own Bookings

**Related Requirement:** FR-14  
**Priority:** High

**Test Steps:**

1. Login as Customer.
2. Open `My Bookings`.

**Expected Result:**

- Only bookings belonging to the authenticated customer are displayed.

---

## TC-22 — Cancel Future Booking

**Related Requirement:** FR-16  
**Priority:** High

**Preconditions:**

- Customer has an eligible future booking.

**Test Steps:**

1. Open the booking.
2. Select `Cancel`.
3. Confirm cancellation.

**Expected Result:**

- Booking status becomes `Cancelled`.

---

## TC-23 — Cancel Completed Booking

**Related Requirement:** FR-16  
**Priority:** High

**Preconditions:**

- Booking status is `Completed`.

**Test Steps:**

1. Attempt to cancel the booking.

**Expected Result:**

- Operation is rejected.
- Booking remains `Completed`.

---

## TC-24 — Reschedule Booking Successfully

**Related Requirement:** FR-17  
**Priority:** Medium

**Preconditions:**

- Booking is eligible for rescheduling.
- New time slot is available.

**Test Steps:**

1. Open booking.
2. Select `Reschedule`.
3. Select another available time.
4. Confirm.

**Expected Result:**

- Booking time is updated.
- New time is stored successfully.

---

## TC-25 — Reschedule Into Conflict

**Related Requirements:** FR-17, FR-12  
**Priority:** High

**Test Steps:**

1. Attempt to reschedule a booking to an occupied conflicting time.

**Expected Result:**

- Rescheduling is rejected.

---

# 8. Booking Status Test Cases

## TC-26 — Confirm Pending Booking

**Related Requirements:** FR-18, FR-19  
**Priority:** Critical

**Preconditions:**

- Booking status is `Pending`.
- Admin is authenticated.

**Test Steps:**

1. Open booking.
2. Confirm booking.

**Expected Result:**

Status changes:

`Pending → Confirmed`

---

## TC-27 — Start Confirmed Service

**Related Requirements:** FR-18, FR-22  
**Priority:** Critical

**Preconditions:**

- Booking is assigned to the mechanic.
- Status is `Confirmed`.

**Test Steps:**

1. Login as assigned mechanic.
2. Select `Start Service`.

**Expected Result:**

Status changes:

`Confirmed → In Progress`

---

## TC-28 — Complete Service

**Related Requirements:** FR-18, FR-23  
**Priority:** Critical

**Preconditions:**

- Booking status is `In Progress`.

**Test Steps:**

1. Select `Complete Service`.

**Expected Result:**

Status changes:

`In Progress → Completed`

---

## TC-29 — Invalid Status Transition

**Related Requirement:** FR-18  
**Priority:** Critical

**Preconditions:**

- Booking status is `Pending`.

**Test Steps:**

1. Attempt to change directly from:

`Pending → Completed`

**Expected Result:**

- Operation is rejected.
- Status remains `Pending`.

---

# 9. Mechanic Test Cases

## TC-30 — View Assigned Jobs

**Related Requirement:** FR-20  
**Priority:** High

**Preconditions:**

- Mechanic has assigned bookings.

**Test Steps:**

1. Login as Mechanic.
2. Open Assigned Jobs.

**Expected Result:**

- Assigned jobs are displayed.
- Unrelated jobs are not displayed unless permitted.

---

## TC-31 — View Daily Jobs

**Related Requirement:** FR-21  
**Priority:** High

**Test Steps:**

1. Login as Mechanic.
2. Open Daily Schedule.

**Expected Result:**

- Jobs for the selected/current date are displayed.

---

## TC-32 — Add Mechanic Comment

**Related Requirement:** FR-24  
**Priority:** Medium

**Test Steps:**

1. Open assigned job.
2. Enter service comment.
3. Save.

**Expected Result:**

- Comment is stored with the correct booking.

---

# 10. Administrator Test Cases

## TC-33 — View All Bookings

**Related Requirement:** FR-27  
**Priority:** High

**Preconditions:**

- Admin is authenticated.

**Test Steps:**

1. Open Booking Management.

**Expected Result:**

- Admin can view bookings across customers.

---

## TC-34 — Assign Mechanic

**Related Requirement:** FR-29  
**Priority:** High

**Preconditions:**

- Booking exists.
- Mechanic account exists.

**Test Steps:**

1. Open booking.
2. Select Mechanic.
3. Save assignment.

**Expected Result:**

- Mechanic is linked to the booking.
- Booking appears in the mechanic's assigned jobs.

---

## TC-35 — Assign Non-Mechanic User

**Related Requirement:** FR-29  
**Priority:** High

**Test Steps:**

1. Attempt to assign a Customer account as mechanic.

**Expected Result:**

- Operation is rejected.

---

# 11. Service History Test Cases

## TC-36 — Completed Service Appears in History

**Related Requirement:** FR-25  
**Priority:** Critical

**Preconditions:**

- Booking has been completed.

**Test Steps:**

1. Login as vehicle owner.
2. Open Service History.

**Expected Result:**

- Completed service is displayed under the correct vehicle.

---

## TC-37 — Cancelled Booking Does Not Appear as Completed History

**Related Requirement:** FR-25  
**Priority:** High

**Preconditions:**

- Booking status is `Cancelled`.

**Test Steps:**

1. Open Service History.

**Expected Result:**

- Cancelled booking is not shown as a completed service record.

---

# 12. Security Test Cases

## TC-38 — Password Is Hashed

**Related Requirement:** NFR-01  
**Priority:** Critical

**Test Steps:**

1. Register a new user.
2. Inspect the user record in PostgreSQL.

**Expected Result:**

- Plain-text password is not stored.
- Stored value is a password hash.

---

## TC-39 — Invalid JWT

**Related Requirement:** NFR-02  
**Priority:** Critical

**Test Steps:**

1. Send protected API request using an invalid token.

**Expected Result:**

- Request is rejected.

---

## TC-40 — Expired JWT

**Related Requirement:** NFR-02  
**Priority:** Critical

**Test Steps:**

1. Use an expired authentication token.
2. Request protected resource.

**Expected Result:**

- Access is rejected.

---

## TC-41 — Secret Files Not Committed

**Related Requirement:** NFR-05  
**Priority:** High

**Test Steps:**

1. Inspect Git repository.
2. Check `.gitignore`.
3. Search tracked files for real credentials.

**Expected Result:**

- Real database passwords and JWT secrets are not present in tracked files.

---

# 13. Performance Test Cases

## TC-42 — Services API Response Time

**Related Requirement:** NFR-06  
**Priority:** Medium

**Test Steps:**

1. Send request to retrieve available services.
2. Measure response time.

**Expected Result:**

Response normally completes within approximately:

`≤ 2 seconds`

under expected demonstration conditions.

---

## TC-43 — Booking API Response Time

**Related Requirements:** NFR-06, NFR-07  
**Priority:** Medium

**Test Steps:**

1. Request available time slots.
2. Measure response time.

**Expected Result:**

Response normally completes within approximately:

`≤ 2 seconds`

under expected demonstration conditions.

---

# 14. Reliability Test Cases

## TC-44 — Invalid Request Does Not Crash Backend

**Related Requirement:** NFR-10  
**Priority:** High

**Test Steps:**

1. Send invalid JSON or invalid input.
2. Send another valid API request afterward.

**Expected Result:**

- Invalid request returns an error.
- Backend remains operational.
- Subsequent valid request succeeds.

---

## TC-45 — Database Operation Failure

**Related Requirement:** NFR-11  
**Priority:** Medium

**Test Scenario:**

Cause or simulate a database operation failure.

**Expected Result:**

- Operation returns an appropriate error.
- Backend does not falsely report success.
- Error can be identified in logs.

---

# 15. Usability Test Cases

## TC-46 — Complete Customer Booking Flow

**Related Requirements:** NFR-12, NFR-13  
**Priority:** High

**Test Steps:**

Complete:

`Login → My Cars → Services → Date → Time → Confirmation`

**Expected Result:**

- User can complete the flow without encountering unclear navigation.
- Required information is visible.
- Actions are understandable.

---

## TC-47 — Error Message Clarity

**Related Requirements:** NFR-14, NFR-29  
**Priority:** Medium

**Test Steps:**

1. Submit invalid form data.
2. Trigger a duplicate email error.

**Expected Result:**

- User sees an understandable error message.
- Raw database errors are not displayed.

---

# 16. Summary

The highest-priority tests are:

- TC-03 — Successful Login
- TC-05 — Protected Endpoint Without Token
- TC-06 — Role Authorization
- TC-11 — Customer Data Isolation
- TC-16 — Booking Creation
- TC-18 — Booking Conflict Prevention
- TC-26 — Booking Confirmation
- TC-27 — Start Service
- TC-28 — Complete Service
- TC-29 — Invalid Status Transition
- TC-36 — Service History
- TC-38 — Password Hashing
- TC-39 — Invalid JWT

These test cases verify the core workflow and the most important security and integrity requirements of the system.