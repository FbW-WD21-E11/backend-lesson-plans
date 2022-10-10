# Lesson Notes

## Security - http / https

Sending plain text passwords over http is a security risk

It presents a risk to a **Man in the middle** attacks

Using the **https** protocol can prevent that
(s = secure)

Get an https certificate [here](https://letsencrypt.org/)

## Authentication

2FA = 2 factor authentication

## Advantages and Disadvantages of JWT

Advantages:

1. Fits within our JavaScript ecosystem - technology familiar to us,
 JSON
2. Removes the responsibility from the server of storing the token

Disadvantages:
1. Little bit slower - because every request MUST include the token
2. Once you've issued the token, it is very hard to remove the validity of the token. You wait to wait until it expires (unless you use **refresh tokens**).

## Storing the JWT

http-cookie

Only the server has access to this

## jsonwebtoken library

We can specify how long a token is valid for using the `expiresIn` option in the method `jwt.sign()`

[Time formats](https://github.com/vercel/ms)

**iat** = issued at (time the token was made)
**exp** = expiry date (time the token is no longer valid)
