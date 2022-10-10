---
title: Presenting - JSON Web Tokens (JWT)
---

# JSON Web Tokens (JWT)

---

## We will cover:

- What are JSON Web Tokens?
- Looking inside a JSON Web Token
- Authentication process
- Authorising a request with JWT

---

## What are JSON Web Tokens?

---

**Authentication versus authorisation**

_Authentication_
Authenticating the username and password, making sure it's correct
> Example:
> Is the username / password correct?

_Authorisation_
Making sure the user that's sending the requests to your server is the same user that logged in
> Example:
> Is the user allowed to perform the action?

---

1. The JWT token is created on the server
2. The JWT token is stored on the client
3. The client uses the JWT token to authorise requests

---

![JWT diagram](./assets/jwt-diagram.png)

---

## Looking inside a JSON Web Token

---

HEADER
> Algorithm and token type

PAYLOAD
> Data

VERIFY SIGNATURE
> The resulting hash of the above

---

## Example JWT

---

**Encoded**

```text
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c
```

---

**Decoded**

Header:
```javascript
{
  "alg": "HS256",
  "typ": "JWT"
}
```

Payload
```javascript
{
    sub: 198239484932482
	iat: "issued at"
	exp: "expired at"
}
```

Verify signature
```javascript
HMACSHA256(
  base64UrlEncode(header) + "." +
  base64UrlEncode(payload),
  SECRET
)
```

---

Verify hash

Creates a hash of all the data on the token, using algorithm and secret.

Further reading: [JWT.io](https://jwt.io/)

Notes:

Try hacking a token!

We can invalidate a token by calculating an expiry time from the issued date.

---

Hashing works a bit like encryption - we take some data and encrypt it

Unlike encryption, there is no key to return the content to its original state - it's a one way process

Once data has changed, the server will know - hashes will not match

Works a bit like password hashing, in that it can't be unhashed.

Notes: Show hashing used with downloadable packages to verify integrity

---

## Authentication process

---

1. Client makes a POST request to the server with { email, password }

2. Server creates a unique JWT for user with secret key. Information about the client is stored in the JWT. Not on the server.

3. Server sends JWT to client, client stores it (localstorage, cookie, etc)

---

## Authorising a request with JWT

---

To send a JWT with a request the client can do one of the following;

1. Attach the JWT to the `Authorization` HTTP header

2. Attach the JWT with a cookie (typically a **http-only** cookie as this is more secure)