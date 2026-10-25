# Employee Management System (Java & MySQL)

A console-based employee management application built with Java, JDBC, and MySQL. It provides an admin login and menu-driven operations for managing employee records.

> **Learning project:** This project is intended for practice and coursework. Review the security notes below before using it with real employee data.

## Features

- Admin login backed by a MySQL table
- Add employee records
- Find an employee by ID
- Show all employee records
- Update an employee's name, department, salary, or phone number
- Delete an employee by ID

## Technology

- Java
- JDBC
- MySQL
- MySQL Connector/J

## Project Structure

```text
EmployeeManagementSystem/
├── src/
│   ├── DBConnection.java
│   ├── Employee.java
│   ├── EmployeeDAO.java
│   └── Main.java
└── database.sql
```

## Setup

1. Install a JDK and MySQL Server.
2. Create a local database user for this project.
3. Review and run `database.sql` in your MySQL client.
4. Configure `src/DBConnection.java` with your local database URL, username, and password.
5. Add MySQL Connector/J to the project's classpath/build path.
6. Run `Main.java` from your IDE or compile and run it using your configured Java environment.

### Database schema note

The Java DAO inserts and reads a `phone` field, but the supplied `database.sql` currently creates the `employees` table without that column. Add the following column before running the employee operations:

```sql
ALTER TABLE employees ADD COLUMN phone VARCHAR(20);
```

If you are creating the database from scratch, include `phone VARCHAR(20)` in the `CREATE TABLE employees` statement instead of running the `ALTER TABLE` command.

## Configuration and Security

- Do not commit real database passwords, API keys, or other secrets to GitHub.
- Configure the MySQL password locally; use environment variables or a local configuration file excluded by `.gitignore` for anything sensitive.
- The current SQL script inserts a default admin login (`admin` / `1234`). Change or remove this default for any deployment, and do not use this simple plaintext-password design for a real system.
- The current authentication code compares the supplied password directly with a database value. For a real application, store salted password hashes and use stronger access-control practices.
- Do not use this learning project to store real employee information until security and data-handling issues have been addressed.

## Current Limitations

- Database connection settings are configured in source code.
- The provided SQL schema is missing the phone column expected by the Java code.
- Password handling is suitable only for a basic demonstration, not production use.

## Purpose

This project is part of my practice with Java, JDBC, SQL, and database-backed CRUD applications.
