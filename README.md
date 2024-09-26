# Spring Boot Microservices with Eureka Service Registry

This repository contains a microservices-based architecture implemented with Spring Boot. It includes four microservices:

1. **School Service** - Manages school-related data.
2. **Student Service** - Manages student-related data.
3. **Service Registry** (Eureka) - A centralized service registry for managing service instances.
4. **API Gateway** - Acts as a single entry point to route requests to the respective services.

---

## Architecture Overview

This microservices architecture follows the following components:

- **Service Registry (Eureka Server)**: Manages service discovery and registration for each microservice.
- **API Gateway**: Routes incoming client requests to the appropriate service based on the URL patterns and acts as a filter for security, rate-limiting, and logging.
- **School Service**: A microservice responsible for managing school-related operations.
- **Student Service**: A microservice responsible for managing student-related operations.
- **Feign Clients**: Used for internal communication between services.

---

## Microservices Structure

The project contains four main modules:

### 1. Service Registry (Eureka Server)
The **Eureka Server** acts as a service registry where all the microservices register themselves. It allows service discovery and registration.
- Port: `8761`
- Path: `/eureka`

### 2. API Gateway
The **API Gateway** acts as a reverse proxy to route requests to the specific microservices based on the route configuration.
- Port: `8080`

### 3. School Service
The **School Service** handles the business logic related to schools.
- Port: `8081`

### 4. Student Service
The **Student Service** handles the business logic related to students.
- Port: `8082`

---

## Prerequisites

Before running the application, make sure you have the following installed:

- **Java 17+** 
- **Maven** 
- **Eureka Server** to manage service registry

---

## How to Run the Project

1. **Clone the Repository**

    ```bash
    git clone https://github.com:ZAID-BAARAB/Spring_Boot-Microservices-Demo.git
    cd Spring_Boot-Microservices-Demo
    ```

2. **Build the Projects**
    Navigate to each microservice directory (e.g., `service-registry`, `school-service`, `student-service`, `api-gateway`) and build them using Maven or Gradle:

    ```bash
    mvn clean install
    ```

3. **Start the Services**
    First, start the Eureka Server:

    ```bash
    cd service-registry
    mvn spring-boot:run
    ```

    Then, start the API Gateway, School Service, and Student Service in separate terminals:

    ```bash
    cd api-gateway
    mvn spring-boot:run

    cd school-service
    mvn spring-boot:run

    cd student-service
    mvn spring-boot:run
    ```

4. **Access the Services**
    - **Eureka Dashboard**: [http://localhost:8761](http://localhost:8761)
    - **API Gateway**: [http://localhost:8080](http://localhost:8080)

---

## API Endpoints

Each microservice exposes the following endpoints:

### School Service (Port: 8081)
- **GET /schools**: Retrieve a list of all schools.
- **GET /schools/{id}**: Retrieve details of a specific school by ID.

### Student Service (Port: 8082)
- **GET /students**: Retrieve a list of all students.
- **GET /students/{id}**: Retrieve details of a specific student by ID.

### API Gateway (Port: 8080)
- **/school-service/**: All requests to the school service are routed via the API Gateway.
- **/student-service/**: All requests to the student service are routed via the API Gateway.

