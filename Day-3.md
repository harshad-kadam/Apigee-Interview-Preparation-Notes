# Apigee-Interview-Preparation-Notes DAY 3
---
1. Some Protocols:
- HTTPS: Secure version of HTTP, adding encryption for secure communication, commonly used for sensitive data exchange.
- WebSockets: Real-time communication protocol for bi-directional data streaming, useful for live updates and push notifications.
- SOAP (Simple Object Access Protocol): XML-based protocol for web service communication, less common than REST due to its complexity, but still used in some legacy systems.
- gRPC (Google Remote Procedure Call): High-performance protocol developed by Google, ideal for low-latency, high-volume data exchange.
- MQTT (Message Queuing Telemetry Transport): Lightweight messaging protocol suitable for machine-to-machine communication and Internet of Things (IoT) applications.
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
---
---
---
---
---
---
---
---
