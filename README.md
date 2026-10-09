# Employee Management REST API

A RESTful Employee Management application built using **Java 21, Spring Boot, Spring Data JPA, and PostgreSQL**. It provides CRUD (Create, Read, Update, Delete) operations for managing employee records through REST APIs.

## Features

- Create a new employee
- Retrieve all employees
- Retrieve an employee by ID
- Update employee details
- Delete an employee
- Store employee records in PostgreSQL
- Automatically generate employee IDs
- Manage database operations using Spring Data JPA

## Technologies Used

| Technology | Purpose |
|---|---|
| Java 21 | Programming language |
| Spring Boot 4.1.1 | Application framework |
| Spring Web MVC | REST API development |
| Spring Data JPA | Database operations |
| Hibernate | ORM and entity management |
| PostgreSQL 18 | Relational database |
| Maven | Dependency management and build |
| Eclipse IDE | Development environment |
| Postman | API testing |

## Project Structure

```text
employee/
├── src/
│   ├── main/
│   │   ├── java/com/tns/
│   │   │   ├── employee/
│   │   │   │   └── EmployeeApplication.java
│   │   │   ├── controller/
│   │   │   │   └── EmployeeController.java
│   │   │   ├── employee/entity/
│   │   │   │   └── Employee.java
│   │   │   ├── repository/
│   │   │   │   └── EmployeeRepository.java
│   │   │   └── service/
│   │   │       └── EmployeeService.java
│   │   └── resources/
│   │       └── application.properties
│   └── test/
├── pom.xml
└── README.md
```

## Prerequisites

Install the following software before running the application:

- Java Development Kit (JDK) 21
- PostgreSQL
- Maven
- Eclipse IDE or another Java IDE
- Postman (for API testing)

## Database Configuration

Create a PostgreSQL database named `employee_db`.

```sql
CREATE DATABASE employee_db;
```

Configure `src/main/resources/application.properties`:

```properties
spring.application.name=employee

spring.datasource.url=jdbc:postgresql://localhost:5432/employee_db
spring.datasource.username=postgres
spring.datasource.password=YOUR_POSTGRES_PASSWORD

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true

server.port=8081
```

Replace `YOUR_POSTGRES_PASSWORD` with your local PostgreSQL password. Never commit actual database passwords to GitHub.

## How to Run

### 1. Clone the repository

```bash
git clone YOUR_GITHUB_REPOSITORY_URL
cd employee
```

Replace `YOUR_GITHUB_REPOSITORY_URL` with your repository URL.

### 2. Configure the database

Create the `employee_db` database and update the PostgreSQL credentials in `application.properties`.

### 3. Run the application

Using Eclipse:

1. Import the project as an existing Maven project.
2. Wait for Maven dependencies to download.
3. Open `EmployeeApplication.java`.
4. Select **Run As → Java Application**.

Alternatively, run from the project directory:

```bash
mvn spring-boot:run
```

The application runs at:

`http://localhost:8081`

## REST API Endpoints

Base URL:

`http://localhost:8081/api/v1/employees`

| HTTP Method | Endpoint | Description |
|---|---|---|
| POST | `/api/v1/employees` | Create an employee |
| GET | `/api/v1/employees` | Retrieve all employees |
| GET | `/api/v1/employees/{id}` | Retrieve an employee by ID |
| PUT | `/api/v1/employees/{id}` | Update an employee |
| DELETE | `/api/v1/employees/{id}` | Delete an employee |

## API Usage Examples

### 1. Create an Employee

**Method:** `POST`

**URL:** `http://localhost:8081/api/v1/employees`

**Request Body:**

```json
{
  "name": "Ravi Kumar",
  "dob": "2002-05-15",
  "salary": 25000,
  "address": "Warangal",
  "designation": "Software Developer"
}
```

Expected response: `201 Created`, with the saved employee details and generated ID.

### 2. Retrieve All Employees

**Method:** `GET`

**URL:** `http://localhost:8081/api/v1/employees`

Expected response: `200 OK`, with a JSON array of employee records.

### 3. Retrieve an Employee by ID

**Method:** `GET`

**URL:** `http://localhost:8081/api/v1/employees/1`

Replace `1` with the employee's actual ID.

Expected response: `200 OK` if the employee exists.

### 4. Update an Employee

**Method:** `PUT`

**URL:** `http://localhost:8081/api/v1/employees/1`

**Request Body:**

```json
{
  "name": "Ravi Kumar Updated",
  "dob": "2002-05-15",
  "salary": 30000,
  "address": "Hyderabad",
  "designation": "Java Developer"
}
```

Expected response: `200 OK` with the updated employee details.

### 5. Delete an Employee

**Method:** `DELETE`

**URL:** `http://localhost:8081/api/v1/employees/1`

Expected response: `204 No Content` when the employee is deleted successfully.

## Employee Data Fields

| Field | Description |
|---|---|
| `id` | Automatically generated employee ID |
| `name` | Employee name |
| `dob` | Date of birth in `YYYY-MM-DD` format |
| `salary` | Employee salary |
| `address` | Employee address |
| `designation` | Employee job designation |

## Testing

Use Postman to test all five REST API endpoints. Verify successful responses and test requests with IDs that do not exist.

## Future Enhancements

- Input validation and meaningful error messages
- Pagination and sorting
- Search employees by name or designation
- Centralized exception handling
- Authentication and authorization
- Automated unit and integration tests

## Author

Developed as a Java Spring Boot project to demonstrate REST API development, database integration, and CRUD operations.

## License

This project is available for learning and educational purposes. Add a license file if you intend to distribute it under a specific open-source license.
