# User Management API

A **Spring Boot 4** RESTful microservice for managing user records. Supports creating, retrieving, and updating users with input validation, DTO-based architecture, and centralized error handling. Packaged with Docker support.

---

## Features

- **Create User** — Register users with validated name and email
- **Get All Users** — Retrieve all users
- **Get User by ID** — Fetch a single user by primary key (404 if not found)
- **Update User** — Modify name and email of an existing user
- **Input Validation** — `@NotBlank` on name, `@Email` on email
- **Global Exception Handling** — Returns field-level validation errors with HTTP 400
- **DTO Architecture** — Clean separation between request DTOs, response DTOs, and JPA entities
- **Docker Support** — Multi-stage Dockerfile with Eclipse Temurin 17

---

## Tech Stack

| Layer        | Technology                       |
|--------------|----------------------------------|
| Language     | Java 17                          |
| Framework    | Spring Boot 4.0.5                |
| Build Tool   | Maven                            |
| Database     | PostgreSQL + Hibernate           |
| Validation   | Jakarta Bean Validation          |
| Boilerplate  | Lombok (compile-time)            |
| Container    | Docker (Eclipse Temurin 17)      |
| Port         | 8081                             |

---

## API Endpoints

| Method | Endpoint      | Description            |
|--------|---------------|------------------------|
| POST   | `/users`      | Create a new user      |
| GET    | `/users`      | Retrieve all users     |
| GET    | `/users/{id}` | Retrieve user by ID    |
| PUT    | `/users/{id}` | Update an existing user|

---

## Sample Requests

**POST /users**

```json
{
  "name": "John Doe",
  "email": "john@example.com"
}
```

**Response (201 Created)**

```json
{
  "id": 1,
  "name": "John Doe",
  "email": "john@example.com"
}
```

---

## Error Handling

**400 Bad Request — Validation Error**

```json
{
  "name": "must not be blank",
  "email": "must be a well-formed email address"
}
```

---

## How to Run

### Locally

```bash
# Prerequisites: Java 17+, Maven 3.8+, PostgreSQL

# 1. Clone
git clone <repo-url>
cd usermanagement

# 2. Configure database
# Set environment variables or use application-dev.properties:
#   DB_URL=jdbc:postgresql://localhost:5432/user_management
#   DB_USERNAME=postgres
#   DB_PASSWORD=your_password

# 3. Build & run
mvn spring-boot:run -Dspring.profiles.active=dev
```

### With Docker

```bash
# Build image
docker build -t user-management-api .

# Run container
docker run -p 8081:8081 \
  -e DB_URL=jdbc:postgresql://host.docker.internal:5432/user_management \
  -e DB_USERNAME=postgres \
  -e DB_PASSWORD=your_password \
  user-management-api
```

---

## Environment Variables

| Variable      | Description                |
|---------------|----------------------------|
| `DB_URL`      | PostgreSQL JDBC URL        |
| `DB_USERNAME` | Database username          |
| `DB_PASSWORD` | Database password          |

---

## Project Structure

```
src/main/java/com/manu/usermanagement/
  UsermanagementApplication.java
  controller/   UserController.java
  service/      UserService.java
  repository/   UserRepository.java
  model/        User.java
  dto/          UserRequest.java, UserResponse.java
  exception/    GlobalExceptionHandler.java

src/main/resources/
  application.properties
  application-dev.properties

Dockerfile
pom.xml
```

---

## Future Improvements

- Add Delete API
- Pagination and sorting
- Swagger / OpenAPI documentation
- Unit and integration tests
- CI/CD pipeline

---

## Author

**Manu Kumar H N**

---

## License

MIT
