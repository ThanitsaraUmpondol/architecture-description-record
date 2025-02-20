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

## Consequences
Pros:Supports high API traffic volumes
 Built-in security mechanisms
 Reduces the burden on backend services

Cons: Requires a database
 Has a learning curve for setup and usage

## Sample code
--
curl -i -X POST http://localhost:8001/services/ \
  --data "name=my-service" \
  --data "url=http://backend-service:8080"
--
