# Non-Functional Requirements

## 1. Purpose

This document defines the non-functional requirements of the project **“Design and Development of a Web-Based Car Service Booking and Management System.”**

Non-functional requirements describe the expected quality characteristics and technical constraints of the system.

The requirements are grouped into:

- Security
- Performance
- Reliability
- Usability
- Maintainability
- Compatibility
- Data Integrity
- Scalability
- Deployment
- Logging and Error Handling

Priority levels:

- **Must Have** — mandatory for the core system
- **Should Have** — important quality requirement
- **Could Have** — optional enhancement

---

# 2. Security Requirements

## NFR-01 — Password Security

**Priority:** Must Have

User passwords shall not be stored in plain text.

### Acceptance Criteria

- Passwords are hashed before being stored in PostgreSQL.
- The original password cannot be retrieved directly from the database.
- Authentication compares the submitted password against the stored password hash.

---

## NFR-02 — Secure Authentication

**Priority:** Must Have

Protected API endpoints shall require authentication.

### Acceptance Criteria

- Unauthorized requests to protected endpoints are rejected.
- A valid authentication token is required for protected functionality.
- Invalid or expired authentication tokens are rejected.

---

## NFR-03 — Role-Based Authorization

**Priority:** Must Have

Access to protected operations shall depend on the authenticated user's role.

### Acceptance Criteria

- Customer users cannot access Admin operations.
- Customer users cannot access Mechanic-only operations.
- Mechanic users cannot access Admin-only operations.
- Role checks are performed on the backend.

---

## NFR-04 — User Data Isolation

**Priority:** Must Have

Users shall not be able to access or modify another customer's private vehicle and booking data without authorization.

### Acceptance Criteria

- A Customer can access only vehicles belonging to their account.
- A Customer can access only their own bookings.
- A Customer cannot modify another user's vehicle or booking by manually changing an API identifier.

---

## NFR-05 — Sensitive Configuration Protection

**Priority:** Must Have

Passwords, database credentials, JWT secrets, and other sensitive configuration values shall not be committed to the Git repository.

### Acceptance Criteria

- Secrets are stored using environment variables.
- `.env` files containing real credentials are excluded through `.gitignore`.
- An example configuration file may contain only placeholder values.

---

# 3. Performance Requirements

## NFR-06 — Normal API Response Time

**Priority:** Should Have

The system should respond to typical API requests within a reasonable time under normal development and demonstration conditions.

### Acceptance Criteria

For common operations such as:

- viewing services;
- viewing customer vehicles;
- viewing bookings;
- retrieving the daily mechanic schedule;

the backend should normally respond within approximately **2 seconds** in the project demonstration environment.

---

## NFR-07 — Booking Availability Response

**Priority:** Should Have

Available time-slot calculation should complete without noticeable delay for the user.

### Acceptance Criteria

- Available slots should normally be returned within approximately 2 seconds under expected project load.
- The frontend provides appropriate loading feedback while availability is being retrieved.

---

## NFR-08 — Efficient Database Queries

**Priority:** Should Have

The backend should avoid unnecessary database operations.

### Acceptance Criteria

- Frequently queried identifiers and foreign keys can be indexed where appropriate.
- Queries should retrieve only required information where practical.
- Repeated database queries inside unnecessary loops should be avoided.

---

# 4. Reliability Requirements

## NFR-09 — Booking Consistency

**Priority:** Must Have

The system shall maintain consistent booking information.

### Acceptance Criteria

- A booking is either successfully stored or rejected.
- Failed booking requests do not create incomplete booking records.
- Booking availability is validated by the backend before a booking is accepted.

---

## NFR-10 — Invalid Request Handling

**Priority:** Must Have

The system shall handle invalid client requests without crashing.

### Acceptance Criteria

- Invalid input produces an appropriate HTTP error response.
- The backend continues running after an invalid request.
- Internal server errors do not expose sensitive implementation information to users.

---

## NFR-11 — Database Failure Handling

**Priority:** Should Have

Database-related errors shall be handled in a controlled manner.

### Acceptance Criteria

- Failed database operations return an appropriate error response.
- Errors are logged for debugging.
- The application does not silently report a failed operation as successful.

---

# 5. Usability Requirements

## NFR-12 — Clear User Navigation

**Priority:** Must Have

The web interface shall provide understandable navigation for the three user roles.

### Acceptance Criteria

Customer users can easily locate:

- My Cars;
- Services;
- Book Service;
- My Bookings;
- Service History.

Mechanics can easily locate:

- assigned jobs;
- daily jobs.

Administrators can easily locate:

- bookings;
- schedule;
- services;
- users;
- mechanics;
- dashboard.

---

## NFR-13 — Booking Process Simplicity

**Priority:** Must Have

The booking process shall follow a clear step-by-step workflow.

### Acceptance Criteria

The customer booking flow follows:

1. Vehicle
2. Service
3. Date
4. Available time
5. Comment
6. Confirmation

The system clearly indicates which stage the user is currently completing.

---

## NFR-14 — User Feedback

**Priority:** Must Have

The interface shall provide feedback after important user actions.

### Acceptance Criteria

The system provides understandable feedback after actions such as:

- successful login;
- failed login;
- vehicle creation;
- booking creation;
- booking cancellation;
- invalid form submission;
- failed server request.

---

## NFR-15 — Responsive Web Interface

**Priority:** Should Have

The application should be usable on common desktop and mobile screen sizes.

### Acceptance Criteria

- Important page content remains accessible on smaller screens.
- Forms remain usable on mobile screen widths.
- Navigation and major actions do not require horizontal page scrolling under expected layouts.

---

# 6. Maintainability Requirements

## NFR-16 — Separation of Responsibilities

**Priority:** Must Have

The application shall use a structured architecture that separates major responsibilities.

### Acceptance Criteria

The frontend and backend are stored as separate project components.

The backend separates responsibilities such as:

- routing;
- request handling;
- business logic;
- database access;
- middleware;
- models.

---

## NFR-17 — Readable Source Code

**Priority:** Should Have

Source code should be understandable and consistently organized.

### Acceptance Criteria

- Functions and variables use meaningful names.
- Large functions are divided where practical.
- Duplicate logic is minimized.
- Code formatting tools are used where applicable.

---

## NFR-18 — Version Control Traceability

**Priority:** Must Have

Project development shall be recorded progressively using Git and GitHub.

### Acceptance Criteria

- Meaningful changes are committed progressively.
- Commit messages reference the related DIP/YouTrack task when applicable.
- Development occurs through task or feature branches.
- Significant changes are merged into `main`.

---

# 7. Compatibility Requirements

## NFR-19 — Modern Browser Support

**Priority:** Should Have

The web application should operate in commonly used modern browsers.

### Acceptance Criteria

The application is tested in at least one Chromium-based browser.

Where practical, major user workflows should also be checked in another modern browser.

---

## NFR-20 — REST/JSON Communication

**Priority:** Must Have

Frontend and backend components shall communicate using JSON over HTTP REST endpoints.

### Acceptance Criteria

- API requests and responses use valid JSON where applicable.
- HTTP methods are used consistently for API operations.
- API responses use appropriate HTTP status codes.

---

# 8. Data Integrity Requirements

## NFR-21 — Relational Integrity

**Priority:** Must Have

Database relationships shall maintain valid references between entities.

### Acceptance Criteria

Relationships are maintained between relevant entities such as:

- User and Car;
- Customer and Booking;
- Mechanic and Booking;
- Car and Booking;
- Service and Booking.

Foreign-key or equivalent application-level constraints prevent invalid references.

---

## NFR-22 — Unique User Identifiers

**Priority:** Must Have

User email and phone information used for registration shall not create duplicate accounts where uniqueness is required.

### Acceptance Criteria

- Duplicate registered email addresses are rejected.
- Duplicate phone numbers are rejected according to the selected registration policy.

---

## NFR-23 — Historical Data Preservation

**Priority:** Must Have

Completed service history shall not be unintentionally lost when related information is modified.

### Acceptance Criteria

- Completed bookings remain available for service-history purposes.
- Deleting or deactivating a service does not silently remove historical completed service records.
- Historical mileage remains associated with the relevant completed booking.

---

# 9. Scalability Requirements

## NFR-24 — Modular Expansion

**Priority:** Should Have

The architecture should allow additional functionality to be introduced without redesigning the complete application.

Possible future functionality includes:

- online payments;
- reminders;
- multimedia attachments;
- inventory management;
- advanced analytics.

### Acceptance Criteria

Major application modules are sufficiently separated so that optional features can be added without replacing the entire architecture.

---

## NFR-25 — Multiple Users

**Priority:** Should Have

The application should support multiple customers, mechanics, vehicles, services, and bookings.

### Acceptance Criteria

The database design does not assume:

- one customer;
- one vehicle;
- one mechanic;
- one service;
- one booking.

---

# 10. Deployment Requirements

## NFR-26 — Containerized Deployment

**Priority:** Should Have

The application should support containerized execution using Docker.

### Acceptance Criteria

Docker configuration can run the main application components.

Expected components include:

- frontend;
- backend;
- PostgreSQL.

---

## NFR-27 — Docker Compose Environment

**Priority:** Should Have

Docker Compose should provide a reproducible local demonstration environment.

### Acceptance Criteria

A documented command can start the required application services.

Configuration required for local development is documented in the repository.

---

# 11. Logging and Error Handling

## NFR-28 — Backend Logging

**Priority:** Should Have

The backend should record useful technical events and errors.

### Acceptance Criteria

Logs provide enough information to investigate:

- failed database operations;
- authentication errors;
- unexpected server errors.

Sensitive information such as user passwords and JWT secrets is not written to logs.

---

## NFR-29 — User-Friendly Error Messages

**Priority:** Should Have

Frontend users should receive understandable error messages instead of raw backend or database errors.

### Acceptance Criteria

For example:

Instead of:

`pq: duplicate key value violates unique constraint users_email_key`

the user should receive a message such as:

`An account with this email already exists.`

---

# 12. Quality Requirement Summary

The highest-priority non-functional requirements are:

- secure password storage;
- JWT authentication;
- backend role authorization;
- customer data isolation;
- protection of credentials;
- booking consistency;
- input validation;
- usable booking workflow;
- relational data integrity;
- maintainable project structure;
- Git traceability.

These requirements provide the minimum quality level expected from the core implementation.