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
|10. what is keycloak auth?|
|:--------------------|

3] error handling for generic and custom error 
-insert into action DB | insert into logs
4] How do you interact with databases 
-Action DB | Transaction DB | GCP logging
5] do you have any microservices in your projects 
- MCS /routingDetails /productDetails /tranAuthDeails /other MCS micro services
6] Apart from development what other tasks 
- Interaction with QA or JAVA or DevOps or Prod Support team
-development, issues tracking with qa's, design architecture discussions, future us analyzations
-Unit  testing, peer review, code merge & deployment, Swagger & SAAD doc, postman collections & structural doc maintenance
-Charge ticket, Shrikants Lead approval, management approval
-Internal, standup, grooming, (downstream & product call if required)
8] which tool for deployment.
-GitHub, POM/edge.json/config.json | 
higher env deployment calls activities--->Change ticket, Rollback & IM plan,branching, merge, devops build(kvm/server)  verification , deployment revision verification, prod support for pointing and manual sensitive data deployment, deployment status updation to lead on regular interval, defect fixing.
9] REST or SOAP 10] When do you create swagger doc & which tool do you use to create it. 
11] How many team members are there in your team 
-Global Payments account with multiple functioning teams | 8 developer members in team including lead

13] How are you comfortable with JS & node 

---
---
|11. Some Protocols:|
|:------------|

---
---
|12. Explain REST|
|:------------|

---
---
|13. What is oauth2?|
|:------------|

---
---
|14. different grant types with deep explanation|
|:------------|

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
- When Interviewer asks any question for me
[ ask for feedback, Apart from apigee what are different technologies with which you will be interacting after joining}  

Achitecture based questions:
- diffrent Apigee component/ Apigee infrastructure 
- function of zookeeper
- Message Processor Concet
- Use of Cancendra in apigee
```
---
---
