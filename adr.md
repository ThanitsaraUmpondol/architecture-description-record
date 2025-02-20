# Use Kong as an API Gateway

## Context  
In this project, we need an API Gateway to manage API Routing, Security, Load Balancing, and Monitoring.
Since the system follows a Microservices Architecture, we require a gateway that supports High Performance & Scalability.

## Decision  
We decided to use Kong API Gateway because:

It supports High Performance and Scalability
It has built-in Authentication & Security features such as OAuth2 and JWT
It provides Load Balancing & Rate Limiting
Additional features can be added via Plugins
It offers both Open Source and Enterprise Editions

## Rationale  
Reasons for choosing Kong over other API Gateways like NGINX or Traefik:

Kong offers higher performance, making it suitable for handling a high volume of API requests
It natively supports OAuth2, JWT, and API Keys without additional development
It provides an Admin API, making API route management easier

Pros:
 Supports high API traffic volumes
 Built-in security mechanisms
 Reduces the burden on backend services

Cons:
 Requires a database (PostgreSQL / Cassandra)
 Has a learning curve for setup and usage

## Sample code
--
```bash
curl -i -X POST http://localhost:8001/services/ \
  --data "name=my-service" \
  --data "url=http://backend-service:8080"

--
# ADR 002: Use Kong JWT Plugin for Authentication  

## Context  
Our API requires an **Authentication & Authorization** system.  
Since the API Gateway handles all API requests, we need to use **JWT Authentication** to reduce the backend's workload.  

## Decision  
We chose **Kong JWT Plugin** for authentication because:  
- It supports **JWT (JSON Web Token)**  
- It validates tokens without needing database queries  
- It allows defining **Consumers & Credentials** directly via Kong  

## Rationale  
Reasons for using **Kong JWT Plugin** instead of other methods:  
- Protects APIs from **Unauthorized Access**  
- Reduces the backend's workload (since the backend doesn't need to validate tokens)  
- Easily integrates with **OAuth2 Providers**  

## Consequences  
**Pros:**  
Reduces backend service workload  
 Increases security (no need to store passwords)  
 Seamlessly integrates with the API Gateway  

**Cons:**  
Requires setting up **JWT Secrets** for each consumer  
 Users need to request a new token when it expires  

## Sample code   
Example of enabling the JWT Plugin in Kong:  

```bash
curl -i -X POST http://localhost:8001/services/my-service/plugins \
  --data "name=jwt"

