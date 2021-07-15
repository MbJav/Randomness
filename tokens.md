# On Tokens
A token is a list claims of something similar to like a receipt of something you bought at the store with the price, date, and what you purchaed. Token works similarly -> way to claim "I am me" or "I am allowed to do this"

## Types of Tokens
### ID Tokens
ID tokens are used by a client to provide a user's identity. This is reffered to as authentication. Ex. client signing into app and being given an ID token on sign-in success. By then having ID token, the client can access resources as the signed in user without prompting the user. ID TOKENS SHOULD NEVER BE USED TO GIVE ACCESS TO SOMETHING. 

### Access Tokens
Access tokens are used by a client to obtain access to additional resources e.g. a protected API such as Google API. This is referred to as authorization. With an access token, you're granted a list of permission against a resource. 

### Refresh Token
refresh tokens can be used with ID and access tokens. Tokens have a fixed lifetime and expire but with a refresh token a client can obtain a token without prompting the user for input. Basic example, user is signed in and using Microsoft Graph with an access token. When that token expires, instead of interrupting the user, a new access token is silently obtained before old access token expires using the original access token. 

### JWTs
Json web tokens -> token is formatted as a JSON object and then base64Url encoded and signed. JWTs can be used for authroization or authentication. Made up of three parts, header, payload, and signature. 
    - payload or body is where the content of the token where the claims are stored. Ex. idenitty of service that issued the token, the subject of token usually user, expiry date, 

JWTs are usually signed with a algo and private key by issuer of token. Yoou can still decode a JWT which is why you shouldn't store sensitive info on it. 

https://techcommunity.microsoft.com/t5/microsoft-365-pnp-blog/introduction-to-tokens/ba-p/2267853 