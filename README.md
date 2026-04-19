# Service Discovery (Netflix Eureka Server)

This project implements a **Service Discovery Server** using **Spring Boot** and **Netflix Eureka**.

The server acts as a **central registry for microservices**, allowing services to dynamically register themselves and discover other services without hardcoding network locations.

This enables **loose coupling**, **scalability**, and **dynamic service communication** in a microservices architecture.

---

## Tech Stack

- Java
- Spring Boot
- Spring Cloud Netflix Eureka Server
- Maven

---

## Architecture Overview

Client services register themselves with the **Eureka Server**, which maintains a registry of all available service instances.
- Microservice A
- Microservice B
- Eureka Service Discovery Server
- Service Registry

Services use this registry to **discover and communicate with each other dynamically**.

---

## Responsibilities of the Service Discovery Server

- Maintain a **centralized service registry**
- Allow microservices to **register themselves automatically**
- Enable **dynamic service discovery**
- Provide **health status of registered services**
- Support **load-balanced communication between services**
- Emit structured logs for operational visibility

---

## Logging and Request Tracking

The registry emits **structured JSON logs** to the console.

- Accepts the `X-Correlation-Id` header on incoming requests
- Generates a correlation ID when the header is missing
- Adds the correlation ID to the logging MDC as `correlationId`
- Includes request lifecycle logs so registry traffic can be correlated with gateway and service logs

Example request header:

```http
X-Correlation-Id: 8f94b4c4-2f6d-4f4b-8d89-7f8e2cb85b67
```

---

## Running the Application

### Build the project

```bash
mvn clean install
```

### Run the application

```bash
mvn spring-boot:run
```

## Eureka Dashboard

Once the server is running, the **Eureka dashboard** can be accessed at:

```text
http://localhost:8761
```

The dashboard shows:

- Registered services
- Service instance details
- Health status of each service

---

## How Service Discovery Works

1. A microservice starts and **registers itself with Eureka Server**
2. Eureka stores the **service instance information**
3. Other services query Eureka to **discover available instances**
4. Client-side load balancing selects a **service instance**

---

## Default Port

| Component | Port |
|----------|------|
| Eureka Server | 8761 |

---

## Future Improvements

- Integrate monitoring using **Spring Boot Actuator**
- Secure the Eureka dashboard and registration endpoints
- Containerize using **Docker**
- Deploy using **Kubernetes**
