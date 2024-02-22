# Apigee-Interview-Preparation-Notes DAY 1
---
1. What is JWT ?
- JWT, or JSON Web Token, is a method used for transferring claims between two parties for authorization purposes.
- header, payload, and signature
- header and payload are base64-encoded strings and can be read by anyone. The signature verifies the payload's integrity
```
1] validation session - stored at server - as userbase increase it inrease servers load to handle session.
2] if server maintains separate DB's to handle session still its servers hop to interact with DB.
3] solution is JWT token for authorization not authentication
```
- use case -to interact with java micro-services
- user provides creads send to target & after badkend success,  generate jwt.

```xml
<VerifyJWT name="JWT-Verify-HS256">
    <DisplayName>JWT Verify HS256</DisplayName>
    <Algorithm>HS256</Algorithm>
    <Source>request.formparam.jwt</Source>
    <IgnoreUnresolvedVariables>false</IgnoreUnresolvedVariables>
    <SecretKey encoding="base64">
        <Value ref="private.secretkey"/>
    </SecretKey>
    <Subject>monty-pythons-flying-circus</Subject>
    <Issuer>urn://apigee-edge-JWT-policy-test</Issuer>
    <Audience>fans</Audience>
    <AdditionalClaims>
        <Claim name="show">And now for something completely different.</Claim>
    </AdditionalClaims>
</VerifyJWT>
```
- [explain how it works  internally](https://www.youtube.com/watch?v=p_sDlCyzUFU)
- [Using a JSON Web Key Set (JWKS) to verify a JWT](https://cloud.google.com/apigee/docs/api-platform/reference/policies/jwt-policies-overview#usingajsonwebkeysetjwkstoverifyajwt).
- [JWKS](https://datatracker.ietf.org/doc/html/rfc7517)

```
<Audience>
<AdditionalClaims>
<AdditionalHeaders>
<IgnoreCriticalHeaders>
<KnownHeaders>
<MaxLifespan>
<JWKS>
```
---
2. XMLtoJSON policy 
```
- use cases 
1] complex xml processing in javascript 
2] access entity response conversion and then attributes processing
<XMLToJSON async="false" continueOnError="false" enabled="true" name="XML-to-JSON-1">
    <DisplayName>XML to JSON 1</DisplayName>
    <Source>response</Source>
    <OutputVariable>response</OutputVariable>
    <Options>
        <RecognizeNumber>true</RecognizeNumber>
        <RecognizeBoolean>true</RecognizeBoolean>
        <RecognizeNull>true</RecognizeNull>
        <NullValue>NULL</NullValue>
        <NamespaceBlockName>#namespaces</NamespaceBlockName>
        <DefaultNamespaceNodeName>&</DefaultNamespaceNodeName>
        <NamespaceSeparator>***</NamespaceSeparator>
        <TextAlwaysAsProperty>true</TextAlwaysAsProperty>
        <TextNodeName>TEXT</TextNodeName>
        <AttributeBlockName>FOO_BLOCK</AttributeBlockName>
        <AttributePrefix>BAR_</AttributePrefix>
        <OutputPrefix>PREFIX_</OutputPrefix>
        <OutputSuffix>_SUFFIX</OutputSuffix>
        <StripLevels>2</StripLevels>
        <TreatAsArray>
            <Path unwrap="true">teachers/teacher/studentnames/name</Path>
        </TreatAsArray>
    </Options>
    <Format>yahoo</Format>
</XMLToJSON>
```
---
3. AccessEntity policy 
```
- access profiles for the following entities:
App
API product
Consumer key
Developer

- Apigee keeps the entities in cache for a minimum of 180 seconds after the entities are accessed.

- [Supported entity types and identifiers](https://cloud.google.com/apigee/docs/api-platform/reference/policies/access-entity-policy#Entities)

- use cases
dynamic behavior, such as conditional endpoint routing, flow execution, policy enforcement.
permission validations 
JAVA microservices customized behaviour based on different api products[visibleToUIApplication]
get entity profile data as XML (or JSON in Apigee hybrid)
```
```xml
<AccessEntity name="GetDeveloperProfile">  || <Source>AccessEntity.GetDeveloperProfile</Source>--> extract var source
  <!-- This is the type entity whose profile we need to pull from the Apigee datastore. -->
  <EntityType  value="developer"/>
  <!-- We tell the policy to use the API key (presented as query parameter) to identify the developer. -->
  <EntityIdentifier ref="request.queryparam.apikey" type="consumerkey"/> 
  <SecondaryIdentifier ref="secondary_identifier" type="identifier_type"/>
</AccessEntity>
```
---
4. AssignMessage policy usage 
- set error messages/ req & res overrring / verb overriding
- headers/ formparams/ queryparams modification
- set variables in flow | use UUID/xerex/base64encode kinda functions
- add/ copy/ remove/ set /AssignTo /AssignVariable
- remove pathsuffix/ authorization data from being sent to target
---
5. BasicAuthentication policy
- alternatively can be done in python policy
- not recomended for sensitive data sharing connection establishment
- Basic Base64EncodedString, Authorization header
- operation encode/decode
- inbound | outbound(store username password in encrypted KVM)
---
6. InvalidateCache policy
```xml
<InvalidateCache async="false" continueOnError="false" enabled="true" name="policy-name">
    <DisplayName>Policy Name</DisplayName>
    <CacheKey>
        <Prefix>prefix_string</Prefix>
        <KeyFragment ref="variable_reference"/>
        <KeyFragment>fragment_string</KeyFragment>
    </CacheKey>
    <!-- Omit this element if you're using the included shared cache. -->
    <CacheResource>cache_to_use</CacheResource>
    <Scope>scope_enumeration</Scope>
    <CacheContext>
        <APIProxyName>application_that_added_the_entry</APIProxyName>
        <ProxyName>proxy_for_which_data_was_cached</ProxyName>
        <TargetName>endpoint_for_which_data_was_cached</TargetName>
    </CacheContext>
    <PurgeChildEntries>true_to_purge_all_child_entries</PurgeChildEntries>
</InvalidateCache>


Real-life use cases of Apigee Invalidate Cache policy:
The Apigee Invalidate Cache policy is a versatile tool for ensuring data freshness in various scenarios. Here are some real-life examples:

1. Updating Product Information:

An e-commerce website uses the Invalidate Cache policy to automatically clear the cache whenever a product's price, description, or availability changes. This ensures customers always see the latest information.
2. Refreshing News Feeds:

A news aggregator platform leverages Invalidate Cache to update its cached feeds immediately when new articles are published. This keeps users informed with the latest news without unnecessary backend calls.
3. Invalidation based on User Actions:

A social media platform utilizes Invalidate Cache to clear a user's profile details cache whenever they update their profile picture or bio. This guarantees users see the updated information instantly.
4. Targeted Cache Invalidation:

A banking application employs Invalidate Cache to remove specific account balance entries from the cache only for users who have recently made transactions. This improves security and data accuracy.
5. Content Management System:

A CMS platform integrates Invalidate Cache to automatically clear cached pages whenever content is edited or published. This ensures visitors always access the latest version of the content.
6. Integration with External Events:

An app uses Invalidate Cache to react to real-time events from external sources. For example, a stock trading app might clear cached stock prices whenever there's a market update.
7. Cache Invalidation on Errors:

An API gateway triggers Invalidate Cache when specific backend errors occur. This prevents outdated data from being served if the initial request failed.
8. Granular Cache Control:

The policy allows fine-grained control over cache invalidation based on conditions like request headers, query parameters, or specific URL patterns. This enables efficient cache management for complex scenarios.
9. Combining with PopulateCache and LookupCache:

Invalidate Cache often works alongside PopulateCache (writing to cache) and LookupCache (reading from cache) to create a comprehensive caching strategy. This optimizes performance while maintaining data freshness.
10. Scalability and Performance:

By strategically invalidating caches, you can reduce backend load and improve overall system performance, especially during peak traffic periods.
Remember, these are just a few examples. The actual use cases will depend on your specific needs and application architecture.
```
---
7. LookupCache & PopulateCache policy
- Used in conjunction with the LookupCache/PopulateCache policy (for writing entries) and the InvalidateCache policy (for invalidating entries).
- lookup & populate cache issue handled for reporting endpoint[avoided duplicate key formation]

- ExpirySettings: TimeoutInSeconds | ExpiryDate | TimeOfDay

| Scope Value | Description | Prefix-for-key |
| :------------|:--------------:|:--------------|
| Global    | Cache key is shared across all API proxies deployed in the environment | orgName__envName__ |
| Application    | API proxy name is used as the prefix. | orgName__envName__proxyName__ |
| Proxy    | ProxyEndpoint configuration is used as the prefix      | orgName__envName__proxyName__deployedRevisionNumber__proxyEndpointName__  |
| Target    | TargetEndpoint configuration is used as the prefix | orgName__envName__proxyName__deployedRevisionNumber__targetEndpointName__  |
| Exclusive    | most specific, and therefore presents minimal risk of namespace collisions | orgName__envName__proxyName__deployedRevisionNumber__proxyEndPntName/TargetEndPntName__  |

---
8. ResponseCache policy
- API's performance
- reduced latency and network traffic
```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<ResponseCache async="false" continueOnError="false" enabled="true" name="Response-Cache-1">
    <DisplayName>Response Cache 1</DisplayName>
    <Properties/>
    <CacheKey>
        <Prefix/>
        <KeyFragment ref="request.uri" />
    </CacheKey>
    <Scope>Exclusive</Scope>
    <ExpirySettings>
        <ExpiryDate/>
        <TimeOfDay/>
        <TimeoutInSeconds ref="flow.variable.here">300</TimeoutInSeconds>
    </ExpirySettings>
    <CacheResource>cache_to_use</CacheResource>
    <CacheLookupTimeoutInSeconds/>
    <ExcludeErrorResponse/>
    <SkipCacheLookup>request.header.bypass-cache = "true"</SkipCacheLookup>
    <SkipCachePopulation/>
    <UseAcceptHeader/>
    <UseResponseCacheHeaders/>
</ResponseCache>
```
---
9. DataCapture policy
- DataCapture policy captures data (such as payload, HTTP headers, and path or query parameters) from an API proxy for use in Analytics.
- Use captured data in custom Analytics reports, as well as to implement sense, monetization, and monitoring rules.
```xml
<DataCapture name="capturepayment" continueOnError="false" enabled="true"> 
  <DisplayName>Data-Capture-Policy-1</DisplayName>
  <IgnoreUnresolvedVariables>false</IgnoreUnresolvedVariables>
  <ThrowExceptionOnLimit>false</ThrowExceptionOnLimit>

  <!-- Existing Variable -->
  <Capture>
    <Collect ref="existing-variable" default="0"></Collect>
    <DataCollector>dc_1</DataCollector>
  </Capture>

  <!-- JSONPayload -->
  <Capture>
    <DataCollector>dc_2</DataCollector>
    <Collect default="0">
      <Source>request</Source>
      <JSONPayload>
        <JSONPath>result.var</JSONPath>
      </JSONPayload>
    </Collect>
  </Capture>

  <!-- URIPath -->
  <Capture>
    <DataCollector>dc_3</DataCollector>
    <Collect default="0">
      <URIPath>
        <!-- All patterns must specify a single variable to extract named $ -->
        <Pattern ignoreCase="false">/foo/{$}</Pattern>
        <Pattern ignoreCase="false">/foo/bar/{$}</Pattern>
      </URIPath>
    </Collect>
  </Capture>
</DataCapture>
```
```
The Apigee DataCapture policy offers a powerful tool for extracting valuable insights from API requests and responses. Here are some real-life use cases showcasing its potential:

Analytics and Reporting:

Track User Behavior: Capture user actions, preferences, and device information to personalize experiences, understand user journeys, and optimize marketing campaigns.
Monitor API Usage: Track API calls by user, application, time, and resource to identify usage patterns, diagnose bottlenecks, and optimize resource allocation.
Generate Custom Reports: Capture specific data points (e.g., error codes, response times) to create customized reports tailored to your business needs.
Security and Fraud Detection:

Audit API Activity: Capture detailed request and response payloads to track API activity, detect suspicious behavior, and prevent unauthorized access.
Identify Malicious Requests: Capture specific data points (e.g., IP addresses, user agents) to identify potential fraud attempts and protect your systems.
Compliance Reporting: Capture relevant data points for regulatory compliance reporting, such as GDPR or PCI DSS.
Monetization and Business Insights:

Track Campaign Performance: Capture data like click-through rates and conversion numbers to measure the effectiveness of marketing campaigns and optimize ROI.
Product Usage Analysis: Capture user interactions with specific product features to understand user preferences and guide product development.
Identify New Revenue Opportunities: Capture user behavior and preferences to identify potential new revenue streams based on user needs and purchasing patterns.
Integration and Data Enrichment:

Capture Data for ETL Pipelines: Extract relevant data from API responses to feed into data warehouses or analytics platforms for further analysis.
Enrich Data for Downstream Applications: Capture specific data points to enrich other applications with valuable information, enhancing their functionality.
Trigger External Actions: Use captured data to trigger actions in other systems, such as sending notifications or updating databases based on specific conditions.
Additional use cases:

A/B Testing: Capture user responses to different API versions to compare performance and measure the effectiveness of changes.
Chatbot Improvement: Capture user interactions with chatbots to improve their understanding of user intent and responses.
API Debugging: Capture detailed error messages and request data to diagnose and resolve API issues more efficiently.
These are just a glimpse into the diverse possibilities of the Apigee DataCapture policy. By understanding your specific needs and data requirements, you can unlock valuable insights and enhance your API ecosystem in various ways. Remember, the chosen use case will determine the specific data points you capture and how you utilize them for your business success.
```
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
---
---

