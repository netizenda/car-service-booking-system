# Technology Comparison

## 1. Purpose

This document compares reasonable technology alternatives for the main technical decisions of the project **“Design and Development of a Web-Based Car Service Booking and Management System.”**

The comparison focuses on four areas:

1. Frontend framework
2. Backend platform and framework
3. Database technology
4. API communication approach

The goal is not to identify a universally “best” technology. The goal is to select technologies that match the requirements, scope, team size, and architecture of the proposed diploma project.

---

# 2. Frontend Framework Comparison

The following frontend technologies were considered:

- React
- Vue
- Angular

## 2.1 React

React is a JavaScript library for building user interfaces using reusable components.

### Strengths

- Component-based architecture
- Strong ecosystem
- Good support for TypeScript
- Suitable for dashboards and interactive forms
- Large number of UI and development libraries
- Straightforward integration with REST APIs
- Flexible project structure

### Limitations

- React itself does not provide a complete application architecture
- Additional libraries may be required for routing, forms, and other functionality
- Developers must make more architectural decisions themselves

### Relevance to the Project

The proposed system contains many reusable interface elements:

- booking forms;
- vehicle cards;
- service cards;
- booking status components;
- mechanic job cards;
- administrator tables and dashboards.

React is well suited to this component-based interface structure.

---

## 2.2 Vue

Vue is a progressive JavaScript framework for building web interfaces.

### Strengths

- Simple and readable syntax
- Component-based architecture
- First-class TypeScript support
- Relatively low learning complexity
- Good documentation
- Suitable for small and medium-sized applications

### Limitations

- Smaller ecosystem than React
- Fewer developers and third-party packages compared with React in some areas
- The team would need to learn and standardize Vue-specific patterns

### Relevance to the Project

Vue is fully capable of implementing the proposed application and would be a reasonable alternative.

---

## 2.3 Angular

Angular is a complete frontend framework with built-in tools for routing, dependency injection, forms, and application architecture.

### Strengths

- Strong TypeScript integration
- Structured architecture
- Built-in routing and form management
- Suitable for large enterprise applications
- Clear conventions for organizing large projects

### Limitations

- Higher learning complexity
- More boilerplate
- Heavier framework for a relatively focused diploma project
- More concepts must be learned before development begins

### Relevance to the Project

Angular would provide strong structure, but the proposed system does not require the complexity typically associated with a large enterprise frontend.

---

## 2.4 Frontend Decision

**Selected technology: React + TypeScript**

### Justification

React was selected because:

- the project contains multiple reusable UI components;
- it integrates naturally with REST APIs;
- TypeScript can be used for type safety;
- it is suitable for both customer-facing pages and dashboards;
- its flexibility matches the size and scope of the project.

Vue would also be a suitable alternative, while Angular introduces more architectural complexity than required.

---

# 3. Backend Platform Comparison

The following backend technologies were considered:

- Go + Gin
- Node.js + Express
- Java + Spring Boot

---

## 3.1 Go + Gin

Go is a statically typed programming language designed for simple and efficient concurrent software.

Gin is a lightweight web framework for Go.

### Strengths

- Static typing
- Simple language syntax
- Good performance
- Built-in concurrency mechanisms
- Fast compilation
- Easy deployment as a compiled binary
- Gin provides straightforward routing and JSON handling
- Well suited to REST API development

### Limitations

- Smaller web-development ecosystem compared with Node.js
- Some higher-level functionality must be implemented explicitly
- Team members may require more familiarity with Go conventions

### Relevance to the Project

The backend mainly requires:

- authentication;
- authorization;
- CRUD operations;
- booking logic;
- database access;
- REST endpoints;
- role-specific business logic.

Go + Gin provides enough functionality without introducing a large framework.

---

## 3.2 Node.js + Express

Node.js allows JavaScript to run on the server.

Express is a minimal web framework commonly used for web APIs.

### Strengths

- Same language can be used on frontend and backend
- Large ecosystem
- Fast development
- Simple REST API creation
- Many authentication and database libraries

### Limitations

- JavaScript applications can become harder to maintain without strict TypeScript usage
- Large dependency trees are common
- Runtime errors may be more common when type safety is not carefully enforced
- CPU-intensive operations require additional architectural consideration

### Relevance to the Project

Node.js + Express would be a strong alternative and could reduce language switching between frontend and backend.

However, the team selected Go in order to use a statically typed backend and a lightweight compiled service.

---

## 3.3 Java + Spring Boot

Spring Boot is a mature framework for building production-grade Java applications.

### Strengths

- Strong type safety
- Mature ecosystem
- Built-in support for dependency injection
- Security ecosystem
- Database integration
- Monitoring and configuration features
- Suitable for complex enterprise systems

### Limitations

- Higher configuration and framework complexity
- More concepts and abstractions
- Heavier development stack
- More boilerplate compared with a small Go service

### Relevance to the Project

Spring Boot would be appropriate for a larger enterprise system, but the proposed diploma system does not require the full complexity of the Spring ecosystem.

---

## 3.4 Backend Decision

**Selected technology: Go + Gin**

### Justification

Go + Gin was selected because:

- the system requires a relatively compact REST backend;
- static typing improves code reliability;
- deployment is straightforward;
- Gin provides the routing and JSON capabilities required by the project;
- Go is suitable for concurrent HTTP services;
- the framework is lightweight enough for the project scope.

Node.js + Express is a reasonable alternative, while Spring Boot provides more enterprise functionality than currently required.

---

# 4. Database Technology Comparison

The following databases were considered:

- PostgreSQL
- MySQL
- MongoDB

---

## 4.1 PostgreSQL

PostgreSQL is an open-source relational database management system.

### Strengths

- Strong relational data model
- Foreign-key constraints
- ACID transactions
- Advanced SQL capabilities
- Strong data integrity
- Support for indexes
- Suitable for complex relationships
- Good compatibility with Go and GORM

### Relevance to the Project

The proposed application contains strongly related entities:

`User → Car → Booking → Service`

Bookings are also connected to:

- customers;
- mechanics;
- services;
- vehicles.

This structure maps naturally to a relational database.

---

## 4.2 MySQL

MySQL is another widely used relational database management system.

### Strengths

- Mature and stable
- Strong SQL support
- Transaction support
- Large ecosystem
- Suitable for typical web applications
- Good performance for common CRUD workloads

### Limitations

For the requirements of this project, MySQL and PostgreSQL provide many similar core capabilities.

The choice therefore depends largely on team preference and specific database features rather than a fundamental inability of MySQL to support the project.

### Relevance to the Project

MySQL would be a valid alternative and could support the required relational structure.

---

## 4.3 MongoDB

MongoDB is a document-oriented NoSQL database.

### Strengths

- Flexible document structure
- Natural storage of nested JSON-like data
- Easy schema evolution in some use cases
- Supports transactions when required

### Limitations

- The project data is strongly relational
- Relationships between users, cars, services, mechanics, and bookings would require a different data modeling approach
- Flexible schemas are not a major requirement for this system
- The relational model of the project makes an SQL database more natural

### Relevance to the Project

MongoDB could implement the application, but its main advantages do not strongly match the requirements of the proposed system.

---

## 4.4 Database Decision

**Selected technology: PostgreSQL**

### Justification

PostgreSQL was selected because:

- project entities have clear relationships;
- foreign keys can enforce data integrity;
- bookings involve multiple related entities;
- transactional consistency is important;
- PostgreSQL integrates with GORM;
- SQL queries are suitable for service history, booking schedules, and administrative statistics.

MySQL would also be suitable, but PostgreSQL was selected as the preferred relational database for the project.

MongoDB was not selected because flexible document storage provides limited benefit for the strongly relational data model.

---

# 5. API Communication Comparison

The following API approaches were considered:

- REST
- GraphQL

---

## 5.1 REST API

REST organizes application functionality around resources and HTTP methods.

Example resources in the proposed system include:

- users;
- cars;
- services;
- bookings.

Example endpoints:

`GET /services`

`GET /cars`

`POST /cars`

`GET /bookings`

`POST /bookings`

`PATCH /bookings/{id}/status`

### Strengths

- Simple conceptual model
- Easy integration with React
- Straightforward testing using Postman
- Predictable endpoints
- Suitable for CRUD operations
- Easy mapping between routes and backend handlers
- Well supported by Gin

### Limitations

- Some interfaces may require multiple API requests
- Endpoints may return more data than a specific screen requires
- API versioning and endpoint organization require planning

---

## 5.2 GraphQL

GraphQL uses a typed schema and allows clients to request specific fields.

### Strengths

- Flexible client queries
- Client can request only required fields
- Strongly typed schema
- Useful for complex and highly connected frontend data requirements

### Limitations

- Additional schema and resolver complexity
- More complex authorization design
- More complicated caching in some scenarios
- More tooling and concepts than required for this project

### Relevance to the Project

The proposed application's resources and operations are predictable.

Most functionality is conventional CRUD and workflow management, so the additional flexibility of GraphQL is not necessary for the initial system.

---

## 5.3 API Decision

**Selected technology: REST API**

### Justification

REST was selected because:

- resources are clearly defined;
- CRUD operations form a major part of the backend;
- REST is straightforward to implement with Gin;
- APIs can be tested easily using Postman;
- frontend/backend communication remains easy to understand and debug;
- the project does not require highly dynamic client-defined queries.

GraphQL is a valid alternative but introduces additional complexity without a clear requirement for that flexibility.

---

# 6. Final Technology Stack

Based on the comparison, the selected stack is:

## Frontend

**React + TypeScript**

Reason:

Component-based user interface with good support for forms, dashboards, and REST integration.

---

## Backend

**Go + Gin**

Reason:

Lightweight, statically typed REST backend with straightforward deployment and good performance.

---

## Database

**PostgreSQL + GORM**

Reason:

Relational database model with strong integrity and clear relationships between system entities.

---

## API

**REST API**

Reason:

Simple and predictable client-server communication suitable for the project's CRUD-oriented resources.

---

## Authentication

**JWT**

JWT will be used to authenticate users and transmit identity information between the frontend and backend.

Authorization rules will distinguish:

- Customer;
- Mechanic;
- Admin.

---

## Deployment

**Docker + Docker Compose**

Docker will be used to provide a reproducible environment for:

- frontend;
- backend;
- PostgreSQL.

---

# 7. Architecture Result

The resulting high-level architecture is:

`React + TypeScript`

`↓ REST / JSON`

`Go + Gin`

`↓ GORM`

`PostgreSQL`

Authentication:

`JWT`

Deployment:

`Docker / Docker Compose`

---

# 8. Conclusion

The technology comparison shows that several alternative stacks could successfully implement the proposed system.

React, Vue, and Angular are all capable frontend technologies. Node.js and Spring Boot are credible backend alternatives. PostgreSQL, MySQL, and MongoDB can all store application data, while REST and GraphQL both provide valid client-server communication models.

The selected technologies were therefore not chosen because the alternatives are incapable of implementing the project.

Instead, **React, Go/Gin, PostgreSQL, and REST API** were selected because together they provide a relatively simple, strongly structured, and technically appropriate architecture for the requirements and scope of the Car Service Booking and Management System.

The selected stack provides enough engineering complexity for the diploma project without introducing unnecessary framework or infrastructure complexity.