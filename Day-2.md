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

