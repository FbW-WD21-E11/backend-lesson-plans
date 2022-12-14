---
title: Presenting - Securing Passwords
theme: 'league'
---

<!-- .slide: data-background="./assets/wallpaper.jpg" -->

# Securing Passwords

---

## We will cover:

- Hashing
- Salt
- Tools
- Authentication flow

---

## Hashing

---

> New words 💡
>
> **hash** - a sequence of letters and numbers, that have been generated by an algorithm from a string. Running the algorithm again will give us the same result.
>
> **hashing** - the process of generating a hash

---

We will not store the password in our database as plain text

We will use a one way **hashing algorithm** to turn the password from plain text into a sequence of seemingly random characters

---

In reality, it is not random, since if we perform the hashing algorithm for a second time, we get the same result.

---

Example:

```
const plainText = 'franco';
const hashed = 'a1305ca10f94f2340770c73e26d427588f236709'; // SHA-1 algorithm
```

---

Hashing is a one way event - we can not (normally) recover the original data, after it has been hashed

---

During login however, the user will send us the password again - we can hash this and compare it with the hashed value we have stored in our database

If the 2 hashes do not match, the passwords do not match

---

> Note: Hashing is not the same as encryption!
> 
> Encryption is reversible, which means (with a key) you can get to the original data
> 
> Hashing is not meant to be reversible - it's a one way process

---

## Salt

---

This is not enough however, because if multiple users have the same password, they will have the exact same hash in the database. This is a security risk.

---

This is why we add "salt" to the hash

We take a random string and add it to the password before we hash it

---

The salt will be different for every single user, meaning all hashes will be different, even if the same password is used

Notes:

If a hacker cracks one password, they can crack other passwords

---

Example:

```
const plainText = 'franco';
const salt = '9dsufoiaf90';
const newPassword = '9dsufoiaf90franco';
const hashed = 'f4dc7556a113cfb3281138e00308fcd0c5d38e66'; // SHA-1 algorithm
```

Much harder to crack!

---

## Tools

---

**bcrypt**

```
npm i bcrypt
```

---

**Generating salt and hash with bcrypt**

```
// the larger the number, the more secure it is (the longer it takes)
const salt = await bcrypt.genSalt(10);

const hashedPassword =  await bcrypt.hash(request.body.password, salt);
```

or we can generate the salt together with the hash

```
const hashedPassword = await bcrypt.hash(request.body.password, 10);
```

---

> bcrypt stores the salt alongside our hashed and salted password, so we do not need to store it separately in our database

---

**Using bcrypt**

with **bcrypt**, we can automatically hash the plain text password we get from the user, and compare the two

```
request.body.password = 'franco';
user.hash = 'a1305ca10f94f2340770c73e26d427588f236709';

bcrypt.compare(request.body.password, user.hash)
```

Returns `true` or `false`

Notes: This function prevents timing attacks

---

## Authentication flow

---

1. User submits username and password to the website

2. We use the username to find the user in our database
   
3. We hash the password sent by the user and compare with hash in database

---

## Questions

Why not hash the password on the client side before sending it to the server?

Typically we would be using HTTPS and that should be encrypting the traffic between the client and the server anyway

Doesn't improve the security - if a hacker can get the password as plain text, they can just as easily get the password as a hash
