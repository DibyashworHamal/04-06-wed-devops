# Event Booking System

## Overview

Event Booking System is a Spring Boot web application for managing events, users, bookings, payments, notifications, and organizer requests. The project uses Thymeleaf for server-side rendering, Spring Security with JWT authentication, Spring Data JPA for persistence, and MySQL as the primary database.

## Key Features

- User registration, login, and profile management
- Event listing, creation, editing, and booking
- Organizer request workflow and admin approval
- Payment handling and booking confirmation
- Event photo upload and file management
- Email notifications using Spring Mail
- Spring Boot Actuator for application monitoring
- Containerized build and deployment support with Docker

## Technology Stack

- Java 21
- Spring Boot 3.3.1
- Spring Data JPA
- Spring Security
- Thymeleaf
- MySQL
- Maven
- Docker / Docker Compose

## Prerequisites

- Java 21 SDK
- Maven 3.9+
- Docker Engine
- Docker Compose
- A MySQL server or container for the application database

## Running Locally

1. Update database settings in `src/main/resources/application.properties` or provide equivalent environment variables.
2. Build the project:

```bash
mvn clean package
```

3. Run the application:

```bash
java -jar target/*.jar
```

4. Open the application in your browser at:

```text
http://localhost:8081
```

> Note: The application properties currently configure `server.PORT=8081`.

## Docker

### Build image

```bash
docker build -t event-booking-system:latest .
```

### Run container

```bash
docker run -p 8081:8081 event-booking-system:latest
```

## Docker Compose

This repository includes a `docker-compose.yml` file that starts the MySQL database and backend service together.

1. Create a `.env` file in the repository root with the required variables.
2. Start the stack:

```bash
docker compose up -d
```

### Example environment variables

```text
DB_IMAGE=mysql:8.0
DB_HOST=db
MYSQL_DATABASE=event_db
MYSQL_USER=admin
MYSQL_PASSWORD=adminpassword
REGISTRY=your-registry
IMAGE_NAME=event-booking-system
IMAGE_TAG=latest
HOST_PORT=8081
CONTAINER_PORT=8081
```

## Configuration

The application uses `src/main/resources/application.properties` for default settings. Important values include:

- `spring.datasource.url`
- `spring.datasource.username`
- `spring.datasource.password`
- `server.PORT`
- `jwt.secret`
- `spring.mail.*`

> Replace any hard-coded credentials with secure values before deploying to production.

## Testing

Run the unit tests with:

```bash
mvn test
```

## CI/CD

This repository also includes Jenkins pipeline definitions:

- `Jenkinsfile.build` — build pipeline
- `Jenkinsfile.deploy` — deployment pipeline

## Notes

- The project includes Thymeleaf templates under `src/main/resources/templates`.
- Static assets are served from `src/main/resources/static`.
- Custom security and authentication are implemented in `src/main/java/np/edu/nast/ebs/config` and `src/main/java/np/edu/nast/ebs/security`.

If you need to customize the database or mail settings, update `application.properties` or provide equivalent environment variable overrides in Docker Compose.
