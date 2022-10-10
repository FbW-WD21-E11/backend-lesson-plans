---
title: Presenting - Authentication & Authorization
theme: "beige"
---

<!-- .slide: data-background="./assets/wallpaper.jpg" -->

# Authentication & Authorization

---

## We will cover:

- What is authentication & authorization?
- How to authenticate a user
- Authorization

---

## What is authentication & authorization?

---

**Authentication** is the process of verifying who a user is

> 🧑🏽 🆔 👮🏼 🏦
> 
> > **Me:** _"My name is Franco Speziali. My password is *******. I want to get into the building please."_
>
> > **Guard** _"That is correct! Please come in."_

---

**Authorization** is the process of verifying what they have access to

> 🧑🏽 📋 👮🏼 💰
> > **Me** _"Hello, I want $500,000 from the vault"_
>
> > **Guard** _"You are not authorized for that amount"_

---

## How to authenticate a user

---

User authentication is crucial to every website

We need a way to verify that a user is who they say they are

It's quite common to do this using a username & password

---

##### Simple example:

1. Client sends a username, password to the server

2. We use the username (which must be unique) to get the user from our database

3. We check the supplied password with the password stored in our database

Sounds simple enough!

---

##### Think security!

- We do not want to store passwords in our database in a readable format (plain text)

- This is a huge security risk

- If a hacker breaks into our database, they have access to all the passwords

Notes:

Unfortunately, people typically use the same password in multiple places

---

## Authorization

---

We don't want to keep asking a user for their username and password, that would get annoying!

We need a way to authorise the user, each time they make a request

There are different ways to do this, but we will focus on token (JWT) based authentication & authorization

---

## Authorization with JWT (JSON Web Tokens)

---

After the user has been authenticated, the server creates a JSON Web Token for that user

The client must send this token for every future request to the server