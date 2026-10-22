# Technology Alternatives

## Purpose

This document identifies alternative technologies for the main
technical decisions of the Car Service Booking and Management System.

The goal is to compare reasonable alternatives before confirming
the final technology stack.

---

## 1. Frontend Framework

Technologies considered:

- React
- Vue
- Angular

Comparison criteria:

- TypeScript support
- Learning complexity
- Ecosystem
- Component-based development
- Suitability for dashboard interfaces
- Integration with REST APIs

---

## 2. Backend Platform and Framework

Technologies considered:

- Go + Gin
- Node.js + Express
- Java + Spring Boot

Comparison criteria:

- Performance
- Development complexity
- REST API development
- Concurrency
- Type safety
- Deployment complexity
- Suitability for the project scope

---

## 3. Database

Technologies considered:

- PostgreSQL
- MySQL
- MongoDB

Comparison criteria:

- Relational data support
- Transactions
- Data integrity
- Relationships
- Query capabilities
- Compatibility with the selected backend
- Suitability for booking and service-history data

---

## 4. API Approach

Technologies considered:

- REST API
- GraphQL

Comparison criteria:

- Architectural complexity
- Ease of implementation
- API testing
- Predictability of endpoints
- Client-server integration
- Suitability for CRUD-based resources

---

## Initial Planned Stack

The current proposed stack is:

- React + TypeScript
- Go + Gin
- PostgreSQL
- REST API

The final choice will be justified after comparing the alternatives.