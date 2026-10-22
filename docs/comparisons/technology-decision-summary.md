# Technology Decision Summary

## 1. Purpose

This document summarizes the final technology decisions for the project **“Design and Development of a Web-Based Car Service Booking and Management System.”**

The selected technologies are based on the comparison of reasonable alternatives and the functional and architectural requirements of the project.

---

## 2. Final Technology Decisions

### Frontend

**Selected:** React + TypeScript

**Alternatives considered:**

- Vue
- Angular

**Reason for selection:**

React provides a component-based architecture suitable for the proposed customer, mechanic, and administrator interfaces.

TypeScript adds static type checking and helps reduce errors when working with API responses, forms, and shared data models.

React is also suitable for:

- booking forms;
- dashboards;
- reusable UI components;
- vehicle and service cards;
- status components;
- REST API integration.

---

### Backend

**Selected:** Go + Gin

**Alternatives considered:**

- Node.js + Express
- Java + Spring Boot

**Reason for selection:**

Go provides static typing, simple deployment, and good performance for HTTP services.

Gin provides the routing, middleware, JSON handling, and REST functionality required for the backend without introducing excessive framework complexity.

The selected backend is suitable for:

- authentication;
- authorization;
- booking business logic;
- CRUD operations;
- status management;
- database access;
- REST API endpoints.

---

### Database

**Selected:** PostgreSQL

**Alternatives considered:**

- MySQL
- MongoDB

**Reason for selection:**

The project has a strongly relational data model.

Main relationships include:

`User → Car`

`User → Booking`

`Car → Booking`

`Service → Booking`

`Mechanic → Booking`

PostgreSQL provides:

- foreign keys;
- transactions;
- relational integrity;
- indexing;
- SQL querying;
- compatibility with GORM.

These capabilities are appropriate for bookings, service history, user data, and administrative statistics.

---

### ORM

**Selected:** GORM

**Reason for selection:**

GORM provides object-relational mapping between Go structures and PostgreSQL tables.

It will be used for:

- model definitions;
- relationships;
- queries;
- database migrations;
- CRUD operations.

---

### API Architecture

**Selected:** REST API

**Alternative considered:**

- GraphQL

**Reason for selection:**

The system contains predictable resources and operations.

Examples include:

- users;
- cars;
- services;
- bookings.

REST provides a simple structure for these resources and is straightforward to implement using Gin and test using Postman.

---

### Authentication

**Selected:** JWT

**Reason for selection:**

JWT will be used to authenticate users and provide identity information for protected API requests.

The backend will use authenticated user information together with role-based authorization.

The system will include three roles:

- Customer
- Mechanic
- Admin

---

### Styling

**Selected:** Tailwind CSS

**Reason for selection:**

Tailwind CSS will be used to create responsive user interfaces while allowing reusable styling patterns without creating a large amount of custom CSS.

---

### Deployment

**Selected:** Docker + Docker Compose

**Reason for selection:**

Docker will provide a consistent environment for running the application.

Docker Compose can coordinate:

- frontend;
- backend;
- PostgreSQL database.

This makes local setup and demonstration easier and reduces environment differences between development computers.

---

## 3. Relationship Between Technologies and Requirements

### Requirement: Multi-role Web Interface

Supported by:

- React;
- TypeScript;
- Tailwind CSS.

---

### Requirement: Secure Authentication and Authorization

Supported by:

- Go;
- Gin middleware;
- JWT;
- backend role checks.

---

### Requirement: Vehicle and Booking Data Relationships

Supported by:

- PostgreSQL;
- GORM.

---

### Requirement: Customer Booking Workflow

Supported by:

- React frontend;
- REST API;
- Go/Gin backend;
- PostgreSQL.

---

### Requirement: Mechanic Job Management

Supported by:

- React dashboard;
- role-based REST endpoints;
- PostgreSQL booking relationships.

---

### Requirement: Administrator Management

Supported by:

- React admin dashboard;
- REST CRUD endpoints;
- backend authorization;
- PostgreSQL.

---

### Requirement: Reproducible Deployment

Supported by:

- Docker;
- Docker Compose.

---

## 4. Final Architecture

The selected architecture is:

`React + TypeScript + Tailwind CSS`

`↓`

`REST API / JSON`

`↓`

`Go + Gin + JWT`

`↓`

`GORM`

`↓`

`PostgreSQL`

Deployment:

`Docker + Docker Compose`

---

## 5. Decision Summary

| Technical Area | Selected Technology |
|---|---|
| Frontend | React + TypeScript |
| Styling | Tailwind CSS |
| Backend | Go + Gin |
| ORM | GORM |
| Database | PostgreSQL |
| API | REST |
| Authentication | JWT |
| Deployment | Docker + Docker Compose |
| API Testing | Postman |
| UI Prototype | Figma |

---

## 6. Conclusion

The selected technology stack is appropriate for the scope and requirements of the proposed diploma project.

The comparison showed that alternative technologies could also implement the system successfully. The final decisions were therefore based on project fit rather than an assumption that the selected technologies are universally superior.

The selected stack provides a clear separation between frontend, backend, and database components while supporting the required booking workflow, user roles, relational data, API communication, and deployment process.