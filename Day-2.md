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

