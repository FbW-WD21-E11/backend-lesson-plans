(jsonwebtoken)         (jsonwebtoken)

Generating the token - Verifying the token



(jsonwebtoken)         (passport.js + passport-jwt)

Generating the token - Verifying the token

## Patterns

Patterns in programming represent a well established structure for solving a problem

`useEffect()` - good example of pub-sub pattern

## Anti-Patterns

Well recognised pattern which represents a bad or inefficient solution to a problem

## Handling the jsonwebtoken

(1)
- Server can send the token as part of the response
- Client sends token through the Authorization header

(2)
- Server can send the token as part of the http-cookie
- Client will send the token as part of the http-cookie

## cookie / http-cookie

The browser has complete control over cookies (browser can read, delete)

The server has complete control over the http-cookie (only the server can read / delete)

## Switching to http-cookie auth

(sending the cookie)

Use `response.cookie()`

(reading the cookie)

1. Install `cookie-parser`
2. Read cookie from jwt.cookies["name of cookie"]
