# Apigee-Interview-Preparation-Notes DAY 3
---
---
1. Some Protocols:
- HTTPS: Secure version of HTTP, adding encryption for secure communication, commonly used for sensitive data exchange.
- WebSockets: Real-time communication protocol for bi-directional data streaming, useful for live updates and push notifications.
- SOAP (Simple Object Access Protocol): XML-based protocol for web service communication, less common than REST due to its complexity, but still used in some legacy systems.
- gRPC (Google Remote Procedure Call): High-performance protocol developed by Google, ideal for low-latency, high-volume data exchange.
- MQTT (Message Queuing Telemetry Transport): Lightweight messaging protocol suitable for machine-to-machine communication and Internet of Things (IoT) applications.
---
---
2. Explain REST
- REST (REpresentational State Transfer) itself is not a protocol, but an architectural style for designing APIs. Here's a breakdown of key concepts related to REST:

|REST Principles/Components:|
|:------------|
|- Client-Server: Applications interact as clients and servers.|
|- Statelessness: Each request contains all necessary information, independent of past requests.|
|- Cacheable: Responses can be cached for improved performance.|
|- Uniform Interface: Resources are identified and manipulated using a common interface (e.g., URLs).|
|- Layered System: Intermediaries can handle requests and responses without affecting functionality.|
|- Code on Demand: Servers can send executable code (e.g., scripts) to clients.|

|Related Concepts:|
|:------------|
|-- HTTP: The most common protocol for RESTful APIs, offering methods like GET, POST, PUT, DELETE, etc.|
|-- HTTPS: Secure version of HTTP, essential for secure data transmission.|
|-- CRUD Operations: Create, Read, Update, and Delete operations for managing resources.|
|-- JSON/XML: Data formats used to exchange information in RESTful APIs.|
|-- RESTful Resources: Entities representing data or functionality, accessed using URLs.|
|-- Representations: Different formats (e.g., JSON, XML) of the same resource.|
|-- Hypermedia: Resources provide links to related resources, enabling navigation.|
|-- API Gateway: Single entry point for managing and securing multiple APIs.|
|-- OAuth: Authentication protocol for secure access control in RESTful APIs.|

|Benefits of REST:|
|:------------|
|-- Simplicity: Easy to understand and implement.|
|-- Scalability: Handles high traffic volumes efficiently.|
|-- Flexibility: Adaptable to various application scenarios.|
|-- Interoperability: Promotes easier communication between different systems.|

|Limitations of REST:|
|:------------|
|-- Security: Requires additional measures for secure communication and data protection.|
|-- Performance: May not be ideal for real-time or high-performance applications.|
|-- Complexity: Can become complex for managing large and intricate APIs.|

|Choosing REST:|
|:------------|
|-- Consider your application's needs, security requirements, and performance demands.|
|-- REST is a good choice for most web-based APIs due to its simplicity and scalability.|
|-- Other protocols like SOAP or gRPC might be better suited for specific scenarios.|
---
---
3.
|What is oauth2?|
|:------------|
|OAuth 2.0 is an open standard for authorization that allows users to share their private resources (e.g. data, files, videos) stored on one site, with another site without having to share their credentials, typically a username and password. It allows a user to grant a third-party application access to their resources on an HTTP service, without sharing their credentials.| 
|OAuth 2.0 is an authorization framework that enables a third-party application to obtain limited access to an HTTP service. It works by allowing the user to grant a third-party application access to their resources on an HTTP service without sharing their credentials. Instead, the user is given a token that the third-party application can use to access the resources on their behalf.|
|OAuth 2.0 is widely used for authentication and authorization by many popular websites and applications such as Google, Facebook, Twitter, Microsoft, and many more.|
|There are several different "grant types" in OAuth 2.0, each of which is used in different situations:|
- Authorization code: used for server-side web applications
- Implicit: used for client-side web applications
- Resource owner password credentials: used for trusted clients
- Client credentials: used for client authentication
- Refresh token: used to refresh an expired access token
---
---
4.
|different grant types with deep explanation|
|:------------|
```
1. Authorization Code Grant:
Description: This is the most common and secure grant type for web applications.

Flow:
User visits the client application and authorizes access to their data on the authorization server.
Authorization server redirects the user back to the client with a temporary "authorization code."
Client sends the code along with its credentials to the authorization server to request an access token.
Authorization server verifies the code and grants an access token if valid.

Benefits:
Secure, as the client never handles the user's access token.
Well-suited for most web application scenarios.

Drawbacks:
Requires server-side communication for exchanging the authorization code for the access token.
```
```
2. Implicit Grant:
Description: Simpler grant type used for browser-based applications like JavaScript widgets.

Flow:
The client redirects the user to the authorization server to obtain an access token.
The user authenticates and authorizes the client.
The authorization server redirects the user back to the client with an access token.

Benefits:
Easier to implement for simple web applications.

Drawbacks:
Less secure as the access token is exposed in the browser's URL or response body.
Not recommended for scenarios requiring high security.
```
```
3. Resource Owner Password Credentials Grant:
Description: Grants access using the user's username and password.

Flow:
User enters their username and password on the client application.
The client application sends the resource owner's credentials to the token endpoint.
The authorization server authenticates the resource owner and issues an access token and a refresh token.

Benefits:
Simple to implement for native mobile applications.

Drawbacks:
Least secure option, exposes user credentials to the client application.
Not recommended for most use cases due to security risks.
```
```
4. Client Credentials Grant:
Description: Enables applications to access resources on their own behalf, not a user.

Flow:
Client sends its credentials directly to the authorization server to request an access token.
Authorization server verifies the credentials and grants an access token if valid.

Benefits:
Useful for server-to-server communication and machine-to-machine interactions.

Drawbacks:
Access token grants access to all resources the client is authorized for, potentially risky.
Limited use cases due to security implications.
```
```
5. Proof Key for Code Exchange (PKCE):
Description: An extension to the Authorization Code Grant, enhancing security by preventing authorization code interception.

Flow:
Similar to Authorization Code Grant, but the client generates a unique code verifier and derives a code challenge from it.
Client sends the code challenge with the authorization request.
Authorization server validates the code verifier when the client exchanges the code for an access token.

Benefits:
Improves security by eliminating the risk of stolen authorization codes.

Drawbacks:
Slightly more complex than the standard Authorization Code Grant.
```
```
Choosing the Right Grant Type:

The best grant type depends on your specific needs and security requirements.
Consider factors like:
Application type: Web, mobile, server-side, etc.
Security level required: How sensitive are the resources being accessed?
User experience: How seamless should the authorization flow be?

By understanding different grant types and their strengths and weaknesses, you can make informed decisions about securing your APIs and protecting user data.
```
---
---
5.
| difference between oauth 1.0 and oauth 2.0|
|:---------------------------|
- Signature Method: OAuth 1.0 uses a signature method to ensure the authenticity of requests, while OAuth 2.0 relies on transport-layer security (TLS) to ensure the authenticity of requests.
- Token types: OAuth 1.0 has two token types: request tokens and access tokens. OAuth 2.0 has several token types such as Bearer tokens, MAC tokens, and JWT tokens.
- Access token format: OAuth 1.0 access tokens are unique, cryptographically signed strings. OAuth 2.0 access tokens can be of any format, but are typically JSON Web Tokens (JWT).
- Token expiration: OAuth 1.0 access tokens never expire, while OAuth 2.0 access tokens have a finite lifetime and can be refreshed.
- Token storage: OAuth 1.0 tokens are stored in the client, while OAuth 2.0 tokens can be stored in the client or on the server.
- Flow: OAuth 1.0 is more complex and has a multi-step flow for obtaining an access token. OAuth 2.0 has a simplified flow and is more flexible.
- Security: OAuth 1.0 is considered less secure than OAuth 2.0 because it uses a signature method which is vulnerable to replay attacks and other types of attacks. OAuth 2.0 is considered more secure because it uses transport-layer security (TLS) to encrypt the communication.
- Support: OAuth 1.0 is being phased out and support for it is being dropped by many providers. OAuth 2.0 is widely supported across the industry and is recommended for new projects.
---
---
6.
|Difference between apigee x & apigee edge|
|:-----------------|
- Apigee X is a cloud-native
```
Availability:
Apigee X: Currently available for new purchase and actively supported by Google Cloud.
Apigee Edge: No longer available for new purchase, but existing users are still supported until March 31, 2025.

Deployment:
Apigee X: Deployed only on Google Cloud Platform (GCP).
Apigee Edge: Could be deployed on GCP or on-premises using Apigee OPDK.

Management:
Apigee X: Fully managed by Google Cloud, including platform updates and infrastructure.
Apigee Edge: Could be managed by Google Cloud (SaaS) or self-managed on-premises (OPDK).

Features:
Apigee X: Offers newer features and enhancements not available in Edge.
Apigee Edge: May lack some newer features, but benefits from a stable platform with long-term support.

Pricing:
Apigee X: Charged based on usage and selected features.
Apigee Edge: Fixed subscription fee for on-premises deployments, pay-as-you-go for SaaS model.
Migration:

Google recommends migrating to Apigee X from Edge to benefit from the latest features and ongoing support.
Tools and resources are available to assist with migration.

Choosing between Apigee X and Edge:
If you are a new user: Choose Apigee X for access to the latest features and full Google Cloud management.
If you are an existing Edge user: Evaluate your needs and migration costs before deciding to migrate to X. Consider factors like feature requirements, budget, and migration complexity.
Additional Resources:

Apigee X vs Apigee Edge: https://www.googlecloudcommunity.com/gc/Apigee/Apigee-X-vs-Apigee-Edge-both-supported-by-Google-what-are-the/m-p/425917
Apigee Edge documentation: https://docs.apigee.com/api-platform/reference/extensions/google-cloud-storage/google-cloud-storage-extension-120
Apigee X documentation: https://cloud.google.com/apigee/docs
Apigee migration resources: https://m.youtube.com/watch?v=ztjXG2_9iaw
```
---
---
7.
|More often seen Http status codes|
|:-----------------|
|200 OK: This code indicates that the request was successful and the requested resource has been returned.|
|201 Created: This code indicates that a new resource has been successfully created in response to a POST request.|
|204 No Content: This code indicates that the request was successful but there is no content to return.|
|400 Bad Request: This code indicates that the request was malformed or invalid. The client should not repeat the request without modification.|
|401 Unauthorized: This code indicates that the request requires authentication and the client has not provided valid credentials.|
|403 Forbidden: This code indicates that the client does not have permission to access the requested resource.|
|404 Not Found: This code indicates that the requested resource could not be found.|
|429 Too Many Requests: This code indicates that the user has sent too many requests in a given amount of time.|
|500 Internal Server Error: This code indicates that an error occurred on the server while processing the request.|
|503 Service Unavailable: This code indicates that the server is currently unable to handle the request due to maintenance or overloading.|
---
---
|what are  preflight requests?|
|:--------------------|

---
