# Spring Boot Config Server

This repository contains the implementation of a **Spring Boot Config Server** for managing and serving externalized configuration properties for distributed applications.

---

## Features
- Centralized configuration management for multiple microservices.
- Support for multiple environments (e.g., `dev`, `qa`, `prod`).
- Integration with Git-based repositories for storing configuration files.
- Dynamic property updates using Spring Cloud Bus (optional).

---

## Prerequisites

- **Java 17** (or later)
- **Maven** (or Gradle, depending on your build tool preference)
- A **Git repository** to store configuration files

---

## Getting Started

### 1. Clone the Repository
```bash
git clone https://github.com/anshulkatta/config-server
cd https://github.com/anshulkatta/config-server
```

### 2. Configure the Application

Update the `application.yml` file to specify the Git repository for storing configurations:

```yaml
server:
  port: 8888

spring:
  cloud:
    config:
      server:
        git:
          uri: https://github.com/your-org/your-config-repo
          default-label: main
```

### 3. Build and Run the Application

#### Using Maven
```bash
mvn clean install
mvn spring-boot:run
```

#### Using Gradle
```bash
gradle build
gradle bootRun
```

---

## Endpoints

### Fetch Configuration
To fetch configuration for a specific application and profile:
```bash
GET http://localhost:8888/{application}/{profile}
```

**Example:**
```bash
GET http://localhost:8888/my-service/dev
```

### Health Check
Check the health of the Config Server:
```bash
GET http://localhost:8888/actuator/health
```

---

## Setting Up Configuration Files
1. Create a Git repository for storing configuration files.
2. Add property files for each application and environment.

**Example:**
```
config-repo/
|-- my-service-dev.properties
|-- my-service-prod.properties
|-- another-service.yml
```



