# User Management API

A RESTful API built using Spring Boot for managing users. It supports creating, retrieving, and updating user data with proper validation and error handling.

## Tech Stack

* Java
* Spring Boot
* Spring Data JPA
* PostgreSQL
* Maven

## Features

* Create User
* Get All Users
* Get User by ID
* Update User
* Input Validation
* Global Exception Handling
* DTO-based architecture

## API Endpoints

### Create User

POST /users

### Get All Users

GET /users

### Get User by ID

GET /users/{id}

### Update User

PUT /users/{id}

## Configuration

This project uses environment variables for database configuration:

* DB_URL
* DB_USERNAME
* DB_PASSWORD

## Running Locally

1. Clone the repository
2. Set up PostgreSQL database
3. Configure application-dev.properties
4. Run the application

## Testing

Use Postman to test the APIs.

## Future Improvements

* Add Delete API
* Pagination
* Swagger Documentation
* Deployment
