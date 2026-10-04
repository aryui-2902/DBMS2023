> **Credit:** Group project (DBMS course, 2023). Original repository: [SaxenaAbhay/DBMS2023](https://github.com/SaxenaAbhay/DBMS2023).

# DBMS2023 – Academic Management System

This is a group project. An academic (school) management system developed after taking suggestions from a real client. Team members are not listed in the source files; see the original repository for contributors.

## What it does

A server-rendered Spring Boot web application backed by MySQL, with session-based login, for managing:

- **Teachers** – name, contact details, joining date, status, salary, subject taught
- **Students** – scholar ID, contact details, date of birth, parent name, session, class
- **Classes** – standard and section, with their students
- **Subjects** – with linked teachers and exams
- **Exams** – date, slot, type, standard, total marks, subject
- **Scores** – marks per student per exam

Each entity has list / create / edit / view pages (e.g. `/teachers`, `/students/new`, `/exams/edit/{id}`), plus search endpoints, user registration, login/logout and password change.

## Tech stack

- Java 21, Spring Boot 3.1 (Web, Data JPA / Hibernate, Validation, DevTools)
- Thymeleaf templates, Bootstrap, jQuery
- MySQL (`mysql-connector-j`)
- Maven (wrapper included), Dockerfile for container builds

## Project layout

```
school-management-sysytem/
  src/main/java/com/dbms/sms/
    controller/   # Authentication, Dashboard, Home, Base controllers
    entity/       # Teacher, Student, Class, Subject, Exam, Score, User
    repository/   # Spring Data JPA repositories
    service/      # Service interfaces + impl/
  src/main/resources/
    templates/    # Thymeleaf pages
    static/       # CSS, JS, images, fonts
```

## Running locally

1. Install JDK 21 and MySQL, then create a database:
   ```sql
   CREATE DATABASE schoolmanagement;
   ```
   Tables are created automatically by Hibernate (`ddl-auto=update`).
2. Set environment variables (credentials are not stored in the repo):
   ```bash
   export DB_URL="jdbc:mysql://localhost:3306/schoolmanagement?useSSL=false&serverTimezone=UTC"
   export DB_USERNAME=root
   export DB_PASSWORD=your_password
   # optional: export PORT=8080
   ```
3. Start the app:
   ```bash
   cd school-management-sysytem
   ./mvnw spring-boot:run
   ```
4. Open http://localhost:8080.
