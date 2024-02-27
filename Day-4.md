# :label::bookmark: Apigee-Interview-Preparation-Notes DAY 4 :high_brightness:
---
---
|1. How many policies in one proxy:|
|:------------|
- varying based on proxy average min 10 to max 45-50, some proxies are having 70+, that was actually wrong aproach of devlopment apigee is an gateway which shouldn't have heavy lifting logics/implementations. this was existing implementation 
- many collaborative discussions happend to decide standards, whatever new proxies we are developing we are trying to avoid/reduce burden of heavy lifting at apigee side. 

---
---
|2. flow callout vs flow hooks|
|:------------|
> Both Flow Callouts and Flow Hooks are powerful mechanisms in Apigee Edge for extending and customizing the behavior of your APIs. However, they serve distinct purposes and operate in different contexts:

> 1. Flow Callout:
```
Description: A policy within a shared flow that allows invoking another shared flow at specific points in the API proxy execution flow.
Purpose: Used to inject reusable functionality from a shared flow into various stages of an API proxy's processing.
Benefits:
-Promotes code reuse and modularity by sharing common logic across multiple API proxies.
-Enables consistent application of policies or transformations at different points in the flow.
-Provides flexibility in controlling when and where to execute specific logic within the API proxy.
Example: permission validations and standard mediation logics like trimming etc, this kina of common logics can be implemented using Flow Callout.
```
> 2. Flow Hook:
```
Description: A configuration option at the environment, proxy, or target level that allows attaching a specific shared flow to be executed at a pre-defined point in the processing flow.
Purpose: Enables applying consistent enforcement of policies or transformations across all API proxies or targets within a defined scope.
Benefits:
-Enforces policies or logic across a group of resources (environments, proxies, or targets) without modifying individual API proxies.
-Simplifies management by centralizing shared logic in a single location.
-Ideal for enforcing broad security requirements or common transformations across your API ecosystem.
Example: You can attach a flow hook to the pre-proxy flow in your environment to enforce authentication for all API proxies deployed in that environment.
```
---
---
|3. can you add error handling logics into post proxy flow hook?|
|:------------|
> shared flow never contains faultrule,
> In the case of larger integration with multiple systems having different formats REST & SOAP we need to handle it at main proxy level.
> because organizations are trying to integrate with multiple partners. they don't know in the upcoming with whom they need to integrate their business and what error standards new partners will be following
> so it's better to keep this at main proxy level.
---
---
|4. Explain Developer portal and how to onboard API’s into the portal?|
|:------------|
> The Apigee Developer Portal acts as a central hub for developers to discover, explore, and utilize APIs offered by your organization. It streamlines the onboarding process by providing a user-friendly interface and simplifies API management for both developers and API providers.

> Here's a breakdown of how the Apigee Developer Portal works:
```
-Develop & Secure API: Build secure API in Apigee Edge.
-Create API Product: Bundle secure API and policies.
-Connect Drupal Portal: Link portal to Apigee Edge.
-Configure Drupal Portal: Set connection and sync details.
-Developer Registration: Create accounts in Drupal portal.
-App Creation & Keys: Developers create apps and get API keys.
-Consume the API: Use keys to access API functionalities.
```

---
---
|5. In case of some unresolvable errors/issues where your lead can't help, what will be your futher action?|
|:---------------------------
```
- Will check first is it for apigee or other technology stack
- will go thorugh community articles for similar issues, will think of alternative approach(as there is always alternative for most of the problems). 
- if apigee then a] with proper analyzation of issue contact google support team for paid organization by creating ticket b] post question on apigee community. 
```
---
---
|6. current project and work & What are daily life different Interactions in project.|
|:-----------------|
```
Methodology: Agile [Release--->sprint]
- project specific explanations
- product requirement comes in the form of features
- BA's create stories in Rally & then story gets pointed accoring to work
- Story analyzation before grooming
- grooming doubts clarifications & prerequisites data gathering for work
- work on story after completion review from leads
- unit JEST & JUNIT testing.
- help collegues if they are stucked
- SAST, DAST & Lint report analyzation.
- SAAD and other business docs completion
- demo to product owner(US clients)
- work on clients feedbacks
- qa deployment & defect fix | prod issues(IM's) work
- collaborate across different teams if they need any help
- sign off
- code push/sync to  higher env (SIT n UAT)
- IM CM create for deployment & approvals
- featues demo to devops | prod support
- IM & Roollback plans go thorugh for devops | prod support
- CERT PROD deployments | support regional deployments for Spring Boot microservices
- after accessful deployment code merging
- [branching strategies, API Naming conventins, Security standards need to be followed along with everything]
```
---
---
|7. How to deploy the proxies and sf's in apigee(different ways)?|
|:-----------------|
```
1. Management UI:
-Easiest method for basic deployments.
-Select revision, choose environment, and confirm.

2. API Tools CLI:
-Offers command-line deployment for automation.
-Requires specific commands and environment details.

3. Management API:
-Enables programmatic deployments via API calls.
-Useful for integration with CI/CD pipelines.

4. Import/Export:
-Export proxies/SFs as bundles for sharing or backup.
-Import bundles into other Apigee environments.
```
---
---
|8. how request flow works in your proxies end to end.|
|:--------------------|
```
-client[mobile(android/ios) | browser(crome/firefox/edge/opera/safari/brave)(windows/linux/unix/macOS/chromeOs)(laptop/desktop/Ipad)]
- Reuqest payloads JSON/XML
-client side loadbalancer/firewall/DNS/TCP handshake/TLS Key & certificate exchanges/iso-osi model_7 layer protocol(https://images.app.goo.gl/SaX2bBPLd5sz1KqE7, https://images.app.goo.gl/84B4AWwepD5bPyZS8)
-multiregions concept--->Gateways(routers--->MP's)--->other apigee components
-VH+basepath+URI component to identify proxy & endpoint & resources/flows operations
-Flow Hooks| base | versioning
-Main Api | policy based securities & validations & transformation of request | Coversion of date, time, country & currency formats if needed
-Target load balancing | algorithms | healthcheck
-Response transformation based on client & target error | fault | success scenario
-DB insertions based on action and any other db's | fault handling using conditional or generic error | log insertion using flow hook
-base api passthrough response | flow hook for logging 
-In general API messages travels through 3 main flows request, response & error
```
---
---
|9. What are different security policies that you are using in your project.?|
|:--------------------|
```
As per xyz company standard & downstream standard
- In flow hooks using spike arrest
- main api | security shared flow based on requirement(oauth | verifyapi key | SOAP msg validation | XML or JSON threat protection | quota & many other)
- for internal api's access control | oauth | Verify api key
- for downstream HMAC | JWT 
```

---
---
|10. Apart from development what are other tasks?|
|:--------------------|
```
-Interaction with QA or JAVA or DevOps or Prod Support team
-development, issues tracking with qa's, design architecture discussions, upcoming features analyzations
-Unit  testing, peer review, code merge & deployment, Swagger & SAAD doc, postman collections & structural doc maintenance
-Charge ticket, Lead approval, management approval
-Internal, standup, grooming, (downstream & product call if required)
-client/devop's/prod team demo's
-collegues help if they are stucked 
```

---
---
|11. which tool/tech/process do you use for deployment?|
|:------------|
```
-GitHub, POM/edge.json/config.json, JFrog to avoid POM versions of previous builds, Jenkins to take build & deploy.
-higher env deployment calls activitiesn[Change ticket, Rollback & IM plan,branching, merge, devops build(kvm/server)  verification]
-deployment revision verification
-prod support for pointing and manual sensitive data deployment
-deployment status updation to lead on regular interval, defect fixing.
```
---
---
|12. key factors of API design|
|:------------|
- Resource Orientation: Use nouns, not verbs, for endpoints.
- HTTP Methods: Map actions to correct HTTP methods.
- Parameters: Use query/path parameters for filtering/sorting.
- HTTP Status Codes: Return correct codes (200, 400, etc).
- Versioning: Strategically version your API for evolution.
- Pagination: Manage large datasets with pagination.
- Data Formats: Support standard formats (JSON, XML).
- Error Handling: Provide clear and informative error messages.
- OpenAPI (Swagger): Define API using OpenAPI specifications.
---
---
|13. Explain Two-Way SSL?|
|:------------|
```
Two-Way SSL: A Secure Handshake
Two-way SSL, also known as mutual authentication, goes beyond the traditional SSL/TLS setup by offering an additional layer of security. Here's how it works:

1. Mutual Verification:
-Both the client (e.g., your web browser) and the server (e.g., the website you're visiting) exchange certificates containing their public keys.
-Each party then uses their private key to digitally sign the received certificate, verifying the other's authenticity.

2. Enhanced Security:
-Compared to one-way SSL, where only the server authenticates itself, two-way SSL provides an additional layer of trust by confirming the client's identity as well.
-This helps prevent unauthorized access attempts and ensures you're communicating with the intended server, mitigating risks like man-in-the-middle attacks.

3. Trusted Communication:
-By establishing mutual trust, two-way SSL creates a secure communication channel where both parties can be confident about who they're interacting with.
-This is especially valuable in scenarios where sensitive data exchange is involved, such as online banking or financial transactions.

In essence, two-way SSL offers a more secure and reliable communication environment by ensuring both parties involved are legitimate and authorized to communicate.
```
---
---
|14. Apigee architecture|
|:------------|
```
breakdown of the Apigee architecture and components, aiming for greater clarity and a focus on the key functionalities:

1] Core Components:
-Message Router: The initial entry point for API traffic. It routes requests to the correct Message Processor, handling load balancing for efficiency.
-Message Processor: The heart of API processing. It executes Apigee policies, mediates backend calls, formats responses, and enforces security and management rules.
-Cassandra Database: A scalable NoSQL database that stores essential runtime data such as API configurations, OAuth tokens, and application keys.
-ZooKeeper: Coordinates distributed configuration information across Apigee components, ensuring consistency and notifying about updates.

2] Management and Development Tools:
-Management Server: Handles administrative API requests, provides a central management interface, and interacts with the UI.
-Apigee UI: A user-friendly web-based interface for building API proxies, managing API products, and handling developer interactions.
-OpenLDAP (Optional): Can be used for user and role management within the Apigee system.

3] Additional Notes:
-Apigee's architecture is designed to be scalable and highly available, supporting the needs of large-scale API deployments.
-The customizable nature of Apigee policies allows for tailoring API behavior to fit specific use cases.
```
---
---
|15. difference between oauth 1.0 and oauth 2.0|
|:---------------------------
---
---
|16. Difference between apigee x & apigee edge|
|:-----------------|

---
---
|17. More often seen Http status codes|
|:-----------------|

---
---
|18. CORS(Cross-Origin Resource Sharing) Concept|
|:--------------------|

---
---
|19. what are  preflight requests?|
|:--------------------|


---
---
|20. Some more Interview topics|
|:--------------------|
```
- What is northbound & sounthbound 
- Raise fault vs route rules 
- removal of api key before sending it to backend 
- diff security proxies 
- Assign msg vs Extract variable 
- different cache policies
- Mediation policies & Security policies[How do we use them]
- Product vs App 
- rate youself in js on the scale of 10
- Why to use dev portal
- What is open Api spec
- Implementation of auth in apigee
- What are sharedflows
- Service callout vs Flow callout
- Benefit of proxy chaining over http calls
- jwt
- rest standards
- flow hooks
- flow call-out
- which version on apigee on Prem or on cloud
- logging
- How much you are comfortable with JS & node JS
- error handling for generic and custom error 
- process of data insertion into action DB | insertion into logs
- How do you interact with databases (using GCP Bigquery(Action DB & Boarding DB | GCP logging)
- What is getting used in company REST or SOAP
- When do you create swagger doc & which tool do you use to create it.
- How many team members are there in your team.
- do you have any microservices in your projects (MCS /routingDetailsData /productDetailsData /tranAuthDeailsData /other MCS micro services)
- When Interviewer asks any question for me
[ ask for feedback, Apart from apigee what are different technologies with which you will be interacting after joining}  


Achitecture based questions:
- diffrent Apigee component/ Apigee infrastructure 
- function of zookeeper
- Message Processor Concet
- Use of Cancendra in apigee
```
---
> [!NOTE]
> Please modify answers based on your experience/need/convinience.
> Also dont hesitate to contribute to add or correct existing questions & answers.
