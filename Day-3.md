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
|8. CORS(Cross-Origin Resource Sharing) Concept|
|:--------------------|
- CORS is a security feature implemented by web browsers that prevents a web page from making requests to a different domain than the one that served the web page. This is done to prevent malicious websites from making unauthorized requests to other sites on behalf of the user.

- When a browser makes a request to a different domain, the server can include a set of headers in its response that indicate which domains are allowed to access the resource. The browser will then check these headers before allowing the request to proceed. If the headers indicate that the domain making the request is not allowed to access the resource, the browser will block the request and the user will not be able to access the resource.

- To enable CORS, a server must include the following headers in its responses:
```
Access-Control-Allow-Origin: This header indicates which domains are allowed to make requests to the resource. It can be set to "*" to allow any domain to make requests, or it can be set to a specific domain.

Access-Control-Allow-Methods: This header indicates which HTTP methods are allowed for the resource.

Access-Control-Allow-Headers: This header indicates which headers are allowed in the request.

Access-Control-Allow-Credentials: This header indicates whether or not the resource allows requests with credentials (e.g. cookies or HTTP authentication)

Access-Control-Max-Age: This header indicate how long (in seconds) the response to the preflight request can be cached.
```
- It's important to note that enabling CORS can introduce security risks, so it's important to be careful when configuring the headers. For example, if the server sets the Access-Control-Allow-Origin header to "*", any domain will be able to make requests to the resource, which could open the server up to cross-site scripting (XSS) attacks.

- CORS can also be bypassed by using a CORS proxy, which is a server that acts as a middleman between the client and the server. The client makes a request to the proxy, which then makes a request to the server on the client's behalf. The server then sends its response to the proxy, which in turn sends the response to the client. This way, the browser doesn't block the request since it's made to the same domain.

---
---
|9. what are  preflight requests?|
|:--------------------|
Preflight requests, also known as CORS (Cross-Origin Resource Sharing) preflight requests, are a crucial mechanism in web security. They act like a "check-in" before a browser sends an actual request to a server from a different domain (origin) than the one that served the initial web page.

Here's a breakdown of preflight requests in depth:

**Purpose:**

* **Security:** Preflight requests ensure the server understands and allows the type of request being sent (e.g., GET, POST, PUT, DELETE) and any custom headers it might include. This prevents potential security vulnerabilities like Cross-Site Request Forgery (CSRF) attacks.
* **Compatibility:** Preflight requests allow the server to inform the browser about its CORS configuration, ensuring the main request is sent only if the server allows it.

**How it works:**

1. **Main Request:** When a browser encounters a resource (e.g., image, script) from a different origin than the current page, it initiates an HTTP request with the desired method (e.g., GET).
2. **Preflight Request:** Before sending the main request, the browser sends an OPTIONS request to the server. This preflight request includes information about:
    * **Origin:** The origin of the page requesting the resource.
    * **Access-Control-Request-Method:** The HTTP method used in the main request (e.g., GET, POST, etc.).
    * **Access-Control-Request-Headers (Optional):** Any custom headers included in the main request.
3. **Server Response:** The server checks its CORS configuration and responds with an OPTIONS response containing specific CORS headers:
    * **Access-Control-Allow-Origin:** Specifies which origins are allowed to access the resource. "*" indicates anyone, or specific origins can be listed.
    * **Access-Control-Allow-Methods (Optional):** Lists the allowed HTTP methods for this resource.
    * **Access-Control-Allow-Headers (Optional):** Lists the allowed custom headers in the request.
    * Other optional CORS headers like `Access-Control-Allow-Credentials` can be included.
4. **Main Request (if allowed):** If the server allows the request based on the preflight response, the browser proceeds with the main request using the original HTTP method.

**Benefits:**

* **Enhanced security:** Protects servers from malicious requests from other origins.
* **Improved compatibility:** Ensures cross-origin requests are handled correctly by servers.

**Limitations:**

* **Additional overhead:** Preflight requests add an extra round-trip to the server, potentially impacting performance.
* **Configuration complexity:** Servers need proper CORS configuration to manage allowed origins, methods, and headers.

**Understanding preflight requests is essential for anyone involved in web development, especially when working with cross-origin resources.** By utilizing this mechanism, you can ensure secure and compatible communication between web applications from different origins.

---
---
|10. what is keycloak auth?|
|:--------------------|
|Keycloak is an open-source identity and access management solution. It provides authentication and authorization services for applications and is often used as an identity provider for microservices and cloud-native applications. Keycloak supports multiple authentication mechanisms, including username and password, OAuth 2.0, OpenID Connect, and SAML. It also provides features such as user management, role-based access control, and Single Sign-On (SSO) across multiple applications. Keycloak can be easily integrated with different types of applications and services, such as web applications, mobile apps, and APIs. This makes it a popular choice for securing microservices and cloud-native architectures.|

---
---
|11. What is the use of API Gateway and why needed?|
|:--------------------|
|API Gateway is a service that sits between a client and a set of microservices. It acts as a reverse proxy, routing requests from clients to the appropriate microservice and then returning the microservice's response to the client. It acts as the only entryway into a system allowing to control security, rate limiting, monitoring statistics and other common cross-cutting concerns.|
|API gateway platforms are used to easily publish, monitor and manage APIs securely. Additionally, API Gateway can handle tasks such as request/response transformation, which allows for a more flexible and decoupled system.|

---
---
|12. About /ping endpoint|
|:--------------------|
|In web APIs, the /ping endpoint is often used as a simple health check endpoint. When a client sends a GET request to the /ping endpoint, the server responds with a simple confirmation that the service is up and running. This can be useful for monitoring the health of an API, as well as for load balancing and failover scenarios.|
|For example, a client could periodically send a GET request to the /ping endpoint to check if the API is available and responding to requests. If the server responds with a 200 status code and a success message, the client knows that the API is healthy and can continue to use it. If the server does not respond, or if it responds with an error status code, the client may assume that the API is down or experiencing issues and may take corrective action, such as switching to a backup server or service.|
|In summary, the /ping endpoint is a simple and lightweight way to monitor the health of an API, and can be used in conjunction with other monitoring and alerting tools to ensure that the API is always available and performing as expected.|

---
---
|13. what is your Daily Work schedule?|
|:--------------------|
```
1]focus mode 2]internal(issues/impedences) 3] QA/other teams help 4]stadups & groomings.
Different activities & responsibilities --->
analyzing future user stories before grooming & list down questions to ask in grooming call
development or enhancement of proxies and sf's and other things like kvm/server if required
support to qa and other teams in case of issues 
UseSrories status update on rally on a regular basis
attend internal standup & grooming calls--daily status, issues & impedances
once development is done peer review
work on suggested changes, again peer review if required.
Unit testing doc
deployment to lower env
Defect fixing if any and parallelly SAAD, collections maintenance and other docs
```

---
---
|14. What is Swagger and why its needed?|
|:--------------------|
```
Swagger (OpenAPI) plays a significant role in the Apigee platform, offering several benefits for API design, development, and management.

1. Standardized API Definition:
Apigee utilizes the OpenAPI Specification as a standard way to define APIs. 

2. Seamless Integration:
Apigee readily integrates with Swagger tools. You can:
Import existing OpenAPI specifications into Apigee as Proxy.
OpenAPI specifications are easily sharable documentation.

3. Enhanced Developer Experience:
By adhering to the OpenAPI standard, understandable for developers familiar with Swagger.
This saves the learning effort and facilitates faster integration and usage of your APIs.

4. interactive Documentation:
Interactive documentation associated with your API proxies.
This ensures developers always have access to up-to-date and accurate information about your APIs.

5. Improved Collaboration:
The standardized and shareable nature of OpenAPI specifications fosters better communication and collaboration between API providers (your team) and consumers (developers using your APIs).
Everyone works from the same blueprint, leading to fewer misunderstandings and a smoother development process.


In summary, Swagger acts as a bridge between developers and your Apigee-managed APIs. By utilizing Swagger and its associated tools, you can:
Standardize API design and documentation.
Improve developer experience and collaboration.
Streamline API development and testing workflows.
Enhance the overall quality and discoverability of your APIs.
```
---
---
|15. what are recent production issues that you have faced?|
|:--------------------|
```
-webhook/json address id fuctionality
-idepotency issue
-xml to json conversion unexpected behaviour for sinle & multiple array element.
```
---
---
|16. some more Interview questions|
|:--------------------|

---
---
|17. Analytics USE?|
|:--------------------|
<img width="901" alt="Analytics" src="https://github.com/harshad-kadam/Apigee-Interview-Preparation-Notes/assets/48818400/ae0be278-baea-43dd-8e65-6d8021a5e276">

```
*API Monitoring

1]Timeline(error & latency alayzations)
-select time-window
-select[environment | region | proxies | targets]
-select[Total Traffic | Errors | Total Latency]

2]Investigate(error & latency wise investigation of errors)

3]Collections (Group API proxies, targets, or dev apps to facilitate monitoring and diagnose issues faster.)

*Events(Monitor and analyze real-time events like):
Example: An API call exceeding a certain threshold for processing time.
Example: A specific error code occurring more frequently than usual.
Example: A security incident like an unauthorized login attempt.

*Alert Rules(Set up automated alerts based on specific criteria to be notified of critical events, such as):
Example: An API proxy experiencing an error rate exceeding 5%.
Example: A backend target becoming unavailable.
Example: TLS certificate expiry notification ahead of time.

*API Metrics
-API Proxy Performance: Analyze overall API proxy performance metrics like:
Example: Throughput (number of requests processed per second)
Example: Errors (number of failed requests)
Example: Average latency (time taken to process a request)
-Cache Performance: Monitor cache hit rates, miss rates, and invalidation events to understand cache effectiveness.
-Error Code Analysis: Understand the distribution and causes of different error codes (e.g., identify if specific error codes are related to specific API calls).
-Latency Analysis: Analyze latency distribution and identify potential bottlenecks by looking at:
Example: Average latency for successful requests vs. failed requests.
Example: Distribution of latency across different API calls or endpoints.
-Target Performance: Monitor the performance of backend targets integrated with the API platform, including:
Example: Response times of backend services.
Example: Resource utilization of backend systems.

*Developers:
-Developer Engagement: Track developer activity and resource utilization, such as:
Example: Number of API proxies created and modified by each developer.
Example: API calls made by developer applications for testing and debugging purposes.
-Traffic Composition: Analyze the source and composition of API traffic, including:
Example: Identify the percentage of traffic coming from mobile devices vs. web browsers.
Example: Track

*End Users
Devices
Geomap

*Custom Reports
Reports
Report Jobs
```
```
From a developer's perspective:
Understanding user behavior: Analyze user interactions with the application to identify usability issues, navigation patterns, and feature usage.
Debugging and performance optimization: Identify performance bottlenecks, diagnose errors, and optimize application code based on real-world data.
A/B testing and experimentation: Measure the impact of changes to the application (e.g., new features, UI changes) by comparing different versions with real user data.
Personalization and user experience: Personalize the application based on user data and preferences to improve engagement and satisfaction.
Data visualization and reporting: Create interactive dashboards and reports to visualize key metrics and insights for internal stakeholders.

From a business perspective:
Customer acquisition and retention: Analyze marketing campaign performance, understand customer acquisition channels, and identify factors influencing customer churn.
Product development and improvement: Use analytics data to guide product development decisions, prioritize features, and ensure products are meeting user needs.
Market research and competitive analysis: Understand market trends, analyze competitor offerings, and identify opportunities for differentiation.
Operational efficiency and cost optimization: Optimize resource allocation, identify areas for cost reduction, and improve operational efficiency based on data-driven insights.
Revenue growth and profitability: Analyze revenue streams, identify opportunities for upselling and cross-selling, and make data-driven decisions to maximize profitability.
Regulatory compliance: Ensure compliance with relevant regulations by capturing and analyzing data related to user activity and transactions.
```

---
---
|18. What are different apigee flows?|
|:--------------------|
```
-Proxy Endpoint (Preflow | Postflow) [request/response]
-Target Endpoint (Preflow | Postflow) [request/response]
-FaultRules/FaultFlow/ErrorFlow
-Postclient Flow(always executes | analytics sent to apigee | logging can also be implemented using this flow)
```

---
---
|19. Exaplin CICD process that you are following?|
|:--------------------|
```
* **For Lower env:**
-create dev branch from master
-create feture branches from dev to work on feature's
-git repo structure
-Local development
-POM versions check using JFrog | configurations for edge & config files (IM plans update acccordingly)
-jenkins thorugh build/configs create | verify created configs on UI
-test and lint execution
-SAST/DAST reports generation
-after that deploy bundle
-cross verify deployment on UI
-inform QA's for deployment completion

* **For Higher Env/Hotfixes:**
-CM tickets 10days prior
-IM/CM plans | Rollback plans
-deployment checklist/and (prod/devops KT's)
-POM versions check using JFrog | decide priority & steps of api's (IM plans update acccordingly)
-configurations for edge & config files | build n deploy via jenkins | verify created configs on UI
-if any deployment fauilure check jenkins logs | to avoid impact rollback steps execution
-help prod and devops with planned activities
-keep informing in groups & QA for deployment completion and other things
-send mail if deployment window extension needed n take approvals
-support regional deployments & higher env issues 
-merge dev branch to master
```
---
---
|20. some more Interview questions|
|:--------------------|
```
- policies: access control, access entity
- What are attributes in apigee their usage,(use case: data needs to be fetched at runtime to decide behaviour of api(different behaviour for diff api consumers))
- Explain KVM & its usage,(encrypted/non-encrypted)
- HTTP vs LocalTargetConnection,
- mTLS setup handson experience, 
- quota vs spike arrest
- security policies used,(VerifyApiKey | XML/Json treat Protection | JWT | HMAC | Regex Protection)
- error codes 404,403,503 when you seen and how you handled
- API specs explanation/swagger,
- Oauth &  different grant types,
- SF in detail,
- Which Apigee version you worked on (SAAS, Hybrid, On-Prem, Multi-cloud)
- about JS policy that you worked on ( api versioning implementation logic | complex payload parsing | logging field's value's customization | best suited for any logic that can not be implemented with apigee out of the box policies)
```
---
