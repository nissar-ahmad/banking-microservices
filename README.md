
# Banking Microservices Project

A robust, production-grade **Banking System** built using **Java 17**, **Spring Boot**, and **Spring Cloud Microservices**. This project demonstrates modern microservice patterns including service discovery, centralized configuration, API gateway routing, inter-service communication, authentication with JWT, and more.

## Project Structure

```
banking-microservices/
├── api-gateway/
├── account-service/
├── authentication-service/
├── common-lib/
├── config-service/
├── customer-service/
├── discovery-service/
├── notification-service/
├── transaction-service/
```

## Modules Overview

- **config-service**: Centralized configuration using Spring Cloud Config Server.
- **discovery-service**: Service registry using Eureka Server.
- **api-gateway**: Acts as a gateway to route requests to various microservices using Spring Cloud Gateway.
- **customer-service**: Handles customer-related operations (CRUD).
- **account-service**: Manages bank accounts, including account creation, update, and retrieval.
- **authentication-service**: Manages user authentication and token generation (Spring Security, JWT).
- **transaction-service**: Handles money transfers and transaction records.
- **notification-service**: Sends notifications via email/SMS for account/transaction events.
- **common-lib**: Contains shared DTOs, utility classes, constants, and error models.

## Tech Stack

- Java 17
- Spring Boot
- Spring Cloud (Eureka, Config, Gateway)
- Spring Security (JWT-based)
- Spring Data JPA
- PostgreSQL / MySQL
- Maven
- Docker (optional)
- OpenFeign / RestTemplate
- Sleuth + Zipkin (optional for tracing)

## How to Run

### 1. Clone the Repo

```bash
git clone https://github.com/your-username/banking-microservices.git
cd banking-microservices
```

### 2. Start Config and Discovery Server

Start config-service first:

```bash
cd config-service
mvn spring-boot:run
```

Start discovery-service (Eureka):

```bash
cd discovery-service
mvn spring-boot:run
```

### 3. Start Other Microservices (in order)

- api-gateway
- authentication-service
- customer-service
- account-service
- transaction-service
- notification-service

> Ensure all services have unique `server.port` in their `bootstrap.yml`

### 4. Accessing Services

- **Eureka Dashboard**: `http://localhost:8761`
- **API Gateway**: `http://localhost:8080`
- Routes like `/api/customer/**`, `/api/account/**`, etc.

## REST Endpoints (Examples)

- `GET /api/customer/all`
- `POST /api/account/create`
- `POST /api/auth/login` (Returns JWT token)
- `POST /api/transaction/transfer`
- `GET /api/notification/history`

## Security

- JWT authentication managed by `authentication-service`
- Other services validate JWT through gateway filters

## Future Enhancements

- Dockerize all services
- Add Swagger UI for each service
- Add Circuit Breaker (Resilience4j)
- Add Zipkin for distributed tracing
