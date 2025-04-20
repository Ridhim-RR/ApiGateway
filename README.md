# API Gateway

This project is a Spring Cloud API Gateway that acts as a single entry point to route client requests to various microservices in a distributed system. It also handles load balancing and service discovery using Eureka.

## 🌐 Overview

The API Gateway is responsible for:

- Routing requests to microservices like Product Service, User Service, Order Service, and Payment Service
- Load balancing requests across service instances using Netflix Ribbon (via Eureka)
- Centralizing cross-cutting concerns like authentication, logging, and security
- Registering itself with Eureka Discovery Server

## 🔁 Load Balancing

All routes use **Eureka service discovery** along with **client-side load balancing**, which means:

- Each service instance registers with the Eureka server
- The gateway uses Eureka to discover service instances dynamically
- Requests are balanced across available instances using the `lb://` URI scheme

## 🔐 Authentication

Authentication is delegated to the **User Service**, which validates tokens for secured endpoints. The gateway forwards authenticated requests downstream to the relevant services.

## 📦 Routed Microservices

| Path Pattern     | Routed To           |
|------------------|---------------------|
| `/products/**`   | Product Service      |
| `/users/**`      | User Service         |
| `/orders/**`     | Order Service        |
| `/payments/**`   | Payment Service      |

## 🧰 Tech Stack

- Java + Spring Boot
- Spring Cloud Gateway
- Eureka Discovery Server
- Load Balancer via Ribbon (through `lb://` URIs)

## 🚀 Run Instructions

1. Make sure Eureka Server and all microservices are up
2. Start the API Gateway
3. Gateway will be available at: `http://localhost:9090`

---

