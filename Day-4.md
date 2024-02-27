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

> 1. Setting Up the Portal:
```
-Configuration: You can configure the portal's appearance, branding, and access control policies to align with your organization's branding and security requirements.
-Content Creation: Create informative content for your APIs, including descriptions, usage examples, documentation, and tutorials. This empowers developers to understand the functionalities and integrate them effectively.
```
> 2. API Onboarding Process:
```
-API Registration: Developers register for the portal and create accounts to access available APIs.
-API Discovery: They can browse through the API catalog, searching and filtering based on various criteria like category, keywords, or tags.
-API Documentation: Once they find an interesting API, they can access detailed documentation, including API reference, code samples, and tutorials, which aid in understanding and integration.
-API Keys and Credentials: Developers can request API keys or credentials needed for authentication and authorization purposes to interact with your APIs.
-Sandbox Environment: In many cases, the portal might offer a sandbox environment where developers can test and experiment with APIs without impacting production environments.
```
> 3. Benefits of the Apigee Developer Portal:
```
-Improved Developer Experience: Provides a centralized platform for discovery, documentation, and access, streamlining the development process.
-Increased API Adoption: Encourages developer engagement and promotes wider adoption of your APIs.
-Simplified API Management: Centralizes API documentation, credentials, and access control, simplifying management for API providers.
-Enhanced Security: Enforces access control policies and facilitates secure authentication and authorization mechanisms.
```
> 4. Additional Considerations:
```
-Analytics and Monitoring: The portal may offer analytics to track developer activity, API usage patterns, and identify areas for improvement.
-Community Features: Some portals include features like forums or chat rooms, fostering communication and collaboration between developers.
-Overall, the Apigee Developer Portal plays a crucial role in creating a positive developer experience and promoting the successful adoption and utilization of your APIs.
```

---
---
|5. difference between oauth 1.0 and oauth 2.0|
|:---------------------------
---
---
|6. Difference between apigee x & apigee edge|
|:-----------------|

---
---
|7. More often seen Http status codes|
|:-----------------|

---
---
|8. CORS(Cross-Origin Resource Sharing) Concept|
|:--------------------|

---
---
|9. what are  preflight requests?|
|:--------------------|

---
---
|10. what is keycloak auth?|
|:--------------------|

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
|20. what is keycloak auth?|
|:--------------------|

---
---
