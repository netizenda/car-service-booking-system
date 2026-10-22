# Architecture Diagrams

This folder contains the main architecture diagrams for the project **“Design and Development of a Web-Based Car Service Booking and Management System.”**

## System Context Diagram

Files:

- `system-context.svg`
- `system-context.mmd`

This diagram shows the system as a single high-level component and its interaction with the three main user roles:

- Customer
- Mechanic
- Admin

It defines the system boundary and summarizes how each role interacts with the system.

## Use Case Diagram

Files:

- `use-case.svg`
- `use-case.mmd`

This diagram shows the main use cases for each user role.

Customer use cases include:

- registration and login;
- vehicle management;
- service browsing;
- booking creation;
- booking management;
- status tracking;
- service history.

Mechanic use cases include:

- viewing assigned jobs;
- viewing the daily schedule;
- viewing vehicle and service details;
- starting and completing services;
- adding service comments.

Admin use cases include:

- service management;
- booking management;
- mechanic assignment;
- user and mechanic management;
- workshop schedule and statistics.

## Component Diagram

Files:

- `component-diagram.svg`
- `component-diagram.mmd`

This diagram shows the main technical components of the system and their interaction.

Main components:

- Web Browser
- React + TypeScript frontend
- Go + Gin backend
- JWT authentication and role authorization
- GORM data access layer
- PostgreSQL database
- Docker and Docker Compose deployment

The frontend communicates with the backend using REST API and JSON.

The backend uses GORM to communicate with PostgreSQL.

## Editable Sources

The `.mmd` files contain editable Mermaid source code.

The `.svg` files are exported visual versions that can be viewed directly in the repository or included in reports and presentations.