# Dummy Microservice

A Spring Boot REST microservice demonstrating full CRUD operations on an Employee resource, backed by an H2 in-memory database with JPA and pre-loaded seed data.

---

## Table of Contents

- [Overview](#overview)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Data Model](#data-model)
- [API Endpoints](#api-endpoints)
- [Getting Started](#getting-started)

---

## Overview

This project demonstrates a simple Spring Boot microservice with a RESTful Employee API. It includes full CRUD — list, get, create, update, and delete — with proper HTTP status codes, exception handling via `@ControllerAdvice`, and an H2 in-memory database pre-loaded with seed data.

---

## Tech Stack

| Tool | Purpose |
|------|---------|
| Spring Boot | Application framework |
| Spring Web | REST controllers |
| Spring Data JPA | Data persistence |
| H2 Database | In-memory database |
| Maven Wrapper | Build tool |

---

## Project Structure

```
dummymicroservice/
└── src/main/java/com/dwiveddi/microservice/
    ├── MicroserviceApplication.java      # Spring Boot entry point
    ├── Employee.java                     # JPA entity (id, name, role, emailId, phoneNumber)
    ├── EmployeeRepository.java           # JpaRepository interface
    ├── EmployeeController.java           # REST controller — full CRUD
    ├── EmployeeNotFoundException.java    # Custom runtime exception
    ├── EmployeeNotFoundAdvice.java       # @ControllerAdvice — returns 404 on not found
    └── LoadDatabase.java                 # CommandLineRunner — seeds Bilbo and Frodo on startup
```

---

## Data Model

### Employee

| Field | Type | Description |
|-------|------|-------------|
| id | Long | Auto-generated primary key |
| name | String | Employee full name |
| role | String | Job role |
| emailId | String | Email address |
| phoneNumber | String | Phone number |

**Seed data (loaded at startup):**
- Bilbo Baggins — burglar
- Frodo Baggins — thief

---

## API Endpoints

| Method | Path | Description |
|--------|------|-------------|
| GET | `/employees` | List all employees |
| GET | `/employees/{id}` | Get employee by ID (404 if not found) |
| POST | `/employees` | Create a new employee |
| PUT | `/employees/{id}` | Replace employee by ID |
| DELETE | `/employees/{id}` | Delete employee by ID |

---

## Getting Started

1. **Run the application**
   ```bash
   ./mvnw clean spring-boot:run
   ```

2. **Test the API**

   ```bash
   # List all employees
   curl -v localhost:8080/employees

   # Get a single employee
   curl -v localhost:8080/employees/1

   # Get a non-existent employee (404)
   curl -v localhost:8080/employees/99

   # Create a new employee
   curl -X POST localhost:8080/employees \
     -H 'Content-type:application/json' \
     -d '{"name":"Samwise Gamgee","role":"gardener","emailId":"sam@gmail.com","phoneNumber":"3333333"}'

   # Update an employee
   curl -X PUT localhost:8080/employees/3 \
     -H 'Content-type:application/json' \
     -d '{"name":"Samwise Gamgee","role":"ring bearer","emailId":"sam@gmail.com","phoneNumber":"3333333"}'

   # Delete an employee
   curl -X DELETE localhost:8080/employees/3
   ```
