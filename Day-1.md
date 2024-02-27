# :label::bookmark: Apigee-Interview-Preparation-Notes DAY 1 :high_brightness:
---
1. AccessControl policy

- request | proxy endpoint

- postback use case

- environment wise diffrent IP's whitelisting

- Google Cloud Armor with Apigee as alternative way to secure your APIs.
https://cloud.google.com/security/products/armor?hl=en

- mask values ,IPv4,  which of the four octets (8, 16, 24, 32 bits)
 
- True-Client-IP header ||  X-Forwarded-For header
```
<ValidateBasedOn>X_FORWARDED_FOR_ALL_IP</ValidateBasedOn>
1)X_FORWARDED_FOR_ALL_IP (default)
2)X_FORWARDED_FOR_FIRST_IP
3)X_FORWARDED_FOR_LAST_IP

<ClientIPVariable>FLOW_VARIABLE</ClientIPVariable>
  
<IgnoreTrueClientIPHeader>true</IgnoreTrueClientIPHeader>
```
- set up a load balancer in front of your Kubernetes cluster

---

2. AssertCondition policy
- assertcondition.policy-name.truthValue
- multiple AssertCondition policies
- fault.name Matches "ConditionEvaluationFailed"
- boolean which can be either a true or a false
- req & res flow

---

3. CORS policy:
- alternative AM & JS
- mechanism that allows JavaScript XMLHttpRequest (XHR) calls executed in a web page to interact with resources from non-origin domains.
- allow all (*)
```xml
child elements of policy:
<AllowCredentials>
<AllowHeaders>
<AllowMethods>
<AllowOrigins>
<DisplayName>
<ExposeHeaders>
<GeneratePreflightResponse>
<IgnoreUnresolvedVariables>
<MaxAge>
```

---

4. DecodeJWT policy
- based on claims we have to tke decision
- eg: if issuer is wrong then dont verify JWT this also can be achieved
<Source>

---

5. ExternalCallout policy
- [external-callout-samples](https://github.com/srinandan/external-callout-samples)
- send gRPC requests to your gRPC server

---

6.[GraphQL policy](https://cloud.google.com/apigee/docs/api-platform/reference/policies/graphql-policy)
- GraphQL policy can parse GraphQL payloads into message flow variables, 
- verify GraphQL requests against a schema
- maximum on the number of fragments allowed
- Child Elements
```xml
<Action>parse|verify|parse-verify</Action>
<MaxDepth>
<MaxCount>
<MaxPayloadSizeInBytes>
<OperationType>[query|mutuation|all]</OperationType>
<Source>
<ResourceURL>
application/graphql | applcation/json
```

---

7. HMAC policy 
- computes || verifies a Hash-based Message Authentication Code (HMAC).
- use case[username+ password+ timestamp+ other details]--> sort & join ---> sha256 ---> security signature[hex]
- uses a cryptographic hash function SHA-1, SHA-224, SHA-256, SHA-384, SHA-512 or MD-5,
- output encoding:hex, base16, base64, base64url
```xml
<Algorithm>
<SecretKey/>
<IgnoreUnresolvedVariables>
<Message>
<Output encoding='base16'>
```

---

8.HTTPModifier policy
-Add | Remove | Set ---> form parameters, headers, or query parameters to a message

---

9.JSONtoXML policy
- source Content-type application/json else policy skipped
- (fault.name Matches "SourceUnavailable")
- (jsontoxml.JSON-to-XML-1.failed = true)
```xml
<Source>
<OutputVariable>
<Options>
```
---

10. OASValidation policy 
- validate request or response against OpenAPI 3.0 Specification (JSON or YAML)
- standard location within the API proxy bundle: apiproxy/resources/oas.
- What content is validated?
Basepath |Path [request path (minus the basepath)] | Verb | Request/response body[application/json] | Parameters	
[ path, header, query and cookie parameters]
```xml
<OASValidation name="myoaspolicy">
   <OASResource>oas://my-spec.json</OASResource>
   <Options>
      <ValidateMessageBody>true</ValidateMessageBody>
      <AllowUnspecifiedParameters>
         <Header>false</Header>
         <Query>false</Query>
         <Cookie>false</Cookie>
      </AllowUnspecifiedParameters>
   </Options>
   <Source>request</Source>
</OASValidation>
```

---

11. PublishMessage policy 
- request is successful, Apigee sets the publishmessage.message.id
- publish your API proxy flow information to a Google Cloud Pub/Sub topic
```xml
<PublishMessage continueOnError="false" enabled="true" name="Publish-Message-1">
    <DisplayName>Publish Message-1</DisplayName>
    <Source>{flow-variable-1}</Source>
    <CloudPubSub>
        <Topic>projects/{flow-variable-project-id}/topics/{flow-variable-topic-name}</Topic>
    </CloudPubSub>
    <IgnoreUnresolvedVariables>true</IgnoreUnresolvedVariables>
</PublishMessage>
```

---

12.RaiseFault policy
- when a specific condition arises
- AM recommended over RF if we dont want to go into error flow 
- after this remaining polcies skipped and flow goes into faultrules
- if asked usage, alternative to store like KVM for non sensitive data.

---

13.ReadPropertySet policy 
-ReadPropertySet policy reads property sets and populates flow variable with the results
```xml
<ReadPropertySet name="read-property-set">
  <Read>
    <Name ref="set-ref">property-set-name</Name>
    <Key ref="key-ref">key-name</Key>
    <AssignTo>var1</AssignTo>
    <DefaultValue>default-value</DefaultValue>
  </Read>
  ...
  <IgnoreUnresolvedVariables>true</IgnoreUnresolvedVariables>
</ReadPropertySet>
```

---

14. SOAPMessageValidation policy
- Validates any XML message against their XSD schemas
- Validates SOAP messages against a WSDL definition
- Determines well-formedness of JSON and XML messages

[DataCapture policy](https://cloud.google.com/apigee/docs/api-platform/reference/policies/data-capture-policy)
```xml
<DataCapture name="DC-1">
    <Capture>
        <DataCollector>dc_data_collector</DataCollector>
        <Collect ref="my_data_variable" /> 
		we can also use fiven elements inside<Collect>--> <Source> | <URIPath>| <QueryParam>| <Header>|<FormParam>|<JSONPayload>|<XMLPayload>
		<JSONPayload>
    </Capture>
</DataCapture>
```

---

15.SpikeArrest policy
- protects against traffic surges with the <Rate> element
- difference between SpikeArrest and Quota
```
- a)spike arrest- denieal of service, bot detection, traffic shaping(backends load handling capacity),
- b)quota -suscription, uasage x transactions per day, metering
-combined use case example of [platinum(5k req/month) & gold(4k req/month) customer --> what if platinum hits all req on same day]
- Quota policies restrict the number of transactions based on business requirements, while spike arrest policies address technical security and availability requirements.
- Spike arrest policies span a short interval of time while a quota policy spans over days, weeks, or months.
- Use cases for a spike arrest policy include denial of service protection and traffic shaping.
- Use cases for a quota policy include subscriptions and usage restrictions based on business requirements.
- Traffic management is a spiked arrest policy use case, while metering is a quota policy use case.
- Both policies may be needed for a customer with different levels of access to transactions, such as a gold and platinum customer.
- The spiked arrest policy can be used to prevent the platinum customer from overwhelming the system with all of their transactions at once.
```

```xml
<SpikeArrest name="Spike-Arrest-1">
  <Rate>12pm</Rate>
  <Identifier ref="client_id" />
  <MessageWeight ref="request.header.weight" />
  <UseEffectiveCount>true</UseEffectiveCount>
</SpikeArrest>
```

---
---
# Add on References 1

- [Conditions reference](https://cloud.google.com/apigee/docs/api-platform/reference/conditions-reference)
 
- [Flow variables reference](https://cloud.google.com/apigee/docs/api-platform/reference/variables-reference)
  
- apigee.metrics.policy.policy_name.timeTaken --> can setup alerts for chances of failures ahead of time.
eg: JS timout | as code gets added with new requirements, JS prcessing time increases.
we just add implementation never consider possibility of failures. 
alearting can be implemented if time taken by particular policy is increasing certain threshold
 
- messageid: globally unique ID |system.timestamp | system.uuid--> uniqueness
  
- below detials can also be logged to get clarity of flow
route.name:The name of the <RouteRule> that was executed in the ProxyEndpoint.
route.target:The name of the TargetEndpoint that was executed.

- PostClientFlow usage

- request & response flow in apigee

- [API proxy configuration reference](https://cloud.google.com/apigee/docs/api-platform/reference/api-proxy-configuration-reference)

- <Authentication> element:
-call a service deployed on Cloud Run as the target using the Authentication element to generate an OpenID Connect token needed to authenticate the call:
https://cloud.google.com/run?hl=en
-call a TargetService that points to the Google Secret Manager service. In this example, the GoogleAccessToken element is configured to generate a Google Auth Token to authenticate the target request

- [properties reference](https://cloud.google.com/apigee/docs/api-platform/reference/endpoint-properties-reference)
success.codes| request.streaming.enabled

- [JavaScript object model](https://cloud.google.com/apigee/docs/api-platform/reference/javascript-object-model)
crypto(get/update/digest)(timestamp) | context

- [Java permission reference](https://cloud.google.com/apigee/docs/api-platform/reference/java-permission-reference)

- [message-template & functions](https://cloud.google.com/apigee/docs/api-platform/reference/message-template-intro)

---
---
# Add on References 2

- [Using Google authentication](https://cloud.google.com/apigee/docs/api-platform/security/google-auth/overview)

- [Masking and hiding data](https://cloud.google.com/apigee/docs/api-platform/security/data-masking)
Updating the mask configuration in an environment using the -API/organizations/{org}/environments/{env}/debugmask
-Hiding sensitive data
-private.
-XML payloads| JSON payloads | Flow variables

- abuse-detection[https://cloud.google.com/apigee/docs/api-security/abuse-detection]

- Looker Studio Integration[https://cloud.google.com/apigee/docs/api-platform/analytics/looker]


- [Using GraphQL](https://cloud.google.com/apigee/docs/api-platform/develop/graphql)

- [Streaming requests and responses](https://cloud.google.com/apigee/docs/api-platform/develop/enabling-streaming)
```
-By default, HTTP streaming is disabled and HTTP request and response payloads are written to a buffer in memory before they are processed by the API proxy pipeline.
-handles very large requests and/or responses
-for non-streamed:Message payload size is restricted to 10 MB. 
-protocol.http.TooBigBody
-not recommended: because can't support issues that arise as a result of exceeding that limit(dont even get logs from google team, if its SAAS version)
-not attach policies that require access to the request or response payload
HTTPProxyConnection & HTTPTargetConnection
      <Property name="response.streaming.enabled">true</Property>
      <Property name="request.streaming.enabled">true</Property>
alternate: Signed URL Generator
```

- [WebSockets](https://cloud.google.com/apigee/docs/api-platform/develop/websocket-config)
```
-web interactions need to happen in real time, such as gaming, communications, financial transactions, and other high-throughput activities.
[websocket-sample](https://github.com/srinandan/websocket-sample)
-protocol that provides a full-duplex communications channel between a web client and web server over a single TCP connection
-Upgrade request header
-101 Switching Protocols
-only use the Verify API Key and OAuthV2 
```

- [create a Java callout](https://cloud.google.com/apigee/docs/api-platform/develop/how-create-java-callout)
```
manipulating request or response messages
Getting and setting flow variables.
Calling external services
Raising faults
Manipulating error messages and status codes
```
- [Integrating with Contact Center AI](https://cloud.google.com/apigee/docs/api-platform/develop/integrating-apigee-contact-center-ai)

- [Performing health checks](https://cloud.google.com/apigee/docs/api-platform/debug/health-check)

- https://status.xxx.com/
  eg: https://status.postman.com/

---

