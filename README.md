# Storefront Service — E-Commerce Microservice

This service is part of a distributed **E-Commerce system** built with **Spring Boot** and **RabbitMQ**.  
The **Storefront** microservice handles product management and communicates with the **Warehouse** service to synchronize stock levels in real time.

---

## Tech & Tools
- **Java 21**
- **Spring Boot**
  - Spring Web
  - Spring Data JPA
  - Spring Validation
- **RabbitMQ** (asynchronous communication)
- **MySQL** (persistence layer)
- **Lombok**
- **ModelMapper**
- **Gradle** (project management)

---

## Architecture Overview
The system follows a **microservice architecture**, where each service is independent and communicates via **RabbitMQ** message queues.

**Storefront responsibilities:**
- Expose REST APIs for product registration and updates.
- Send stock update messages to the **Warehouse** via RabbitMQ.
- Manage product data persistence through MySQL and JPA.

---

## 📁 Project Structure
```bash
src/
└── main/
├── java/br/com/dio/storefront/
│   ├── config/        # RabbitMQ and environment configuration
│   ├── controller/    # REST controllers (API endpoints)
│   ├── dto/           # Data Transfer Objects
│   ├── entity/        # JPA entities
│   ├── mapper/        # Entity ↔ DTO mappers
│   ├── repository/    # Spring Data repositories
│   └── service/       # Business logic and message consumers
└── resources/
├── application.yml
└── application-dev.yml
```

---

## Getting Started

### Prerequisites
- Java 21+
- Gradle
- RabbitMQ server running (default port 5672)

### Build & Run
```bash
# clone the repository
git clone https://github.com/raphichos/storefront.git
cd storefront

#Configure your database and RabbitMQ credentials
src/main/resources/application.yml

# build and run
./gradlew bootRun

#access the API endpoint at:
http://localhost:8080/warehouse
```

---

## Communication Flow
Storefront Service --(Message: StockStatusMessage)--> [RabbitMQ Queue] --> [Warehouse Service]

---

Developer - Raphael Rios
