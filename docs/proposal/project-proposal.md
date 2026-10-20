# Project Proposal

## 1. Project Title

**Design and Development of a Web-Based Car Service Booking and Management System**

## 2. Team Members

- Makazhanov Danial — Frontend Developer / UI
- Qanatuly Madi — Backend and Database Developer

**Supervisor:** To be specified

---

## 3. Problem Statement

Car service appointments may be managed through phone calls,
messaging applications, or other manual communication methods.
Such a process may make it less convenient for customers to check
available appointment times and keep information about their
previous vehicle services in one place.

From the car service side, managing appointments, customer
vehicles, service statuses, and schedules through separate or
manual processes can also make information management more
difficult.

The proposed project will address this problem by providing a
single web-based system where customers can book car service
appointments and where car service employees can manage the
booking process.

The assumptions in this problem statement will be further
validated through discussions with potential users.

---

## 4. Target Users

The system has three main user groups:

### Customer

A car owner who wants to:

- create an account;
- add and manage vehicles;
- view available car services and prices;
- select an available appointment date and time;
- create or cancel a booking;
- track booking status;
- view vehicle service history.

### Mechanic

A car service employee who wants to:

- view assigned service jobs;
- view information about the customer's vehicle;
- update the status of a service job;
- add comments about completed work.

### Administrator

A car service administrator who wants to:

- manage users and mechanics;
- manage available services and prices;
- manage bookings;
- manage the service schedule;
- assign or manage service appointments;
- view basic system statistics.

---

## 5. Project Aim

The aim of the project is to design and develop a web-based
car service booking and management system that provides customers
with an online appointment booking process and provides car service
staff with tools for managing appointments and service information.

---

## 6. Project Objectives

The objectives of the project are:

1. To design a web-based system with Customer, Mechanic,
   and Administrator roles.

2. To implement secure user registration and authentication
   using JWT.

3. To implement vehicle management that allows customers
   to add and manage multiple vehicles.

4. To develop a catalogue of car services containing service
   descriptions, prices, and estimated duration.

5. To implement an appointment booking process where customers
   can select a vehicle, service, date, and available time slot.

6. To implement booking status management using the following
   workflow:

   Pending → Confirmed → In Progress → Completed

   The system will also support Cancelled bookings.

7. To maintain service history for customer vehicles.

8. To develop a mechanic interface for viewing assigned jobs
   and updating their status.

9. To develop an administrator dashboard for managing users,
   services, bookings, mechanics, and schedules.

10. To test the main functional and security requirements
    of the developed system.

---

## 7. Expected Outcomes

The expected result of the project is a functional web application
for car service booking and management.

The system is expected to provide:

- user registration and authentication;
- role-based access for customers, mechanics, and administrators;
- customer vehicle management;
- car service catalogue;
- appointment booking using available time slots;
- booking status tracking;
- vehicle service history;
- mechanic job management;
- administrative management functionality;
- persistent storage of application data.

The final system should demonstrate the complete workflow from
customer booking creation to completion of the service appointment.

---

## 8. Project Scope

### In Scope

The project will include:

- Web-based user interface
- User registration and login
- JWT authentication
- Role-based authorization
- Customer vehicle management
- Service catalogue
- Service prices and duration
- Appointment booking
- Available time-slot selection
- Booking cancellation
- Booking status management
- Vehicle service history
- Mechanic dashboard
- Administrator dashboard
- Basic statistics
- REST API
- PostgreSQL database
- Docker-based deployment

### Out of Scope

The initial project will not include:

- Online payment processing
- AI-based vehicle diagnostics
- Spare-parts marketplace
- GPS vehicle tracking
- Native Android or iOS applications
- Integration with external accounting systems
- Integration with external payment systems

These functions may be considered as possible future extensions
but are not part of the initial diploma project scope.

---

## 9. Proposed Technology Stack

### Frontend
- React
- TypeScript
- Tailwind CSS

### Backend
- Go
- Gin
- GORM

### Database
- PostgreSQL

### Authentication
- JWT

### Architecture
- REST API

### DevOps
- Docker
- Docker Compose

### Development Tools
- GitHub
- YouTrack
- Postman
- Figma

The final selection of technologies will be justified separately
through the technology comparison required by the project
evaluation criteria.