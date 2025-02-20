# Title
Use Kong JWT Plugin for Authentication  

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

```bash
curl -i -X POST http://localhost:8001/services/my-service/plugins \
  --data "name=jwt"
