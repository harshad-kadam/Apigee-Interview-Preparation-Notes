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
Promotes code reuse and modularity by sharing common logic across multiple API proxies.
Enables consistent application of policies or transformations at different points in the flow.
Provides flexibility in controlling when and where to execute specific logic within the API proxy.
Example: You might have a shared flow for security checks and another for logging. A flow callout can be used to invoke the security check flow before routing the request to the backend and then invoke the logging flow after receiving the response.
```
> 2. Flow Hook:
```
Description: A configuration option at the environment, proxy, or target level that allows attaching a specific shared flow to be executed at a pre-defined point in the processing flow.
Purpose: Enables applying consistent enforcement of policies or transformations across all API proxies or targets within a defined scope.
Benefits:
Enforces policies or logic across a group of resources (environments, proxies, or targets) without modifying individual API proxies.
Simplifies management by centralizing shared logic in a single location.
Ideal for enforcing broad security requirements or common transformations across your API ecosystem.
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
|4. different grant types with deep explanation|
|:------------|

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
