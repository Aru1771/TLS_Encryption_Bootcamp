TLS Handshake (How HTTPS Actually Works)
===========================================


This is a very common 4–5 years DevOps interview topic.

🎯 Goal

By the end of today, you'll understand:

Why TLS Handshake is needed
Client Hello
Server Hello
Certificate Exchange
Certificate Validation
Session Key Generation
Encrypted Communication
TLS 1.2 vs TLS 1.3 Handshake
Complete Production Flow


Before Starting
---------------
Imagine a user opens:

https://myapp.company.com

Question:

How do the browser and server start talking securely?

They have never communicated before.

They don't have a shared password.

So how do they create a secure connection?

The answer is:
------------------
TLS Handshake


Step 1 – User Opens the Website
--------------------------------
Browser

↓

https://myapp.company.com

The browser says:

"I want to establish a secure connection."


Step 2 – Client Hello
----------------------------
The browser sends the first message.

Browser

↓

Client Hello

The Client Hello contains:
--------------------------
TLS Version

Supported Cipher Suites

Random Number (Client Random)

Supported Extensions

SNI (Server Name Indication)

Example:
----------
Client Hello

TLS 1.3

AES256

CHACHA20

Client Random = XYZ123

Think of it as:

"Hello Server, I support TLS 1.3 and these encryption algorithms."

Step 3 – Server Hello
------------------------
The server replies:
---------------------
Server

↓

Server Hello

It selects:

TLS Version

Cipher Suite

Server Random

Example:
---------
TLS Version = TLS 1.3

Cipher = AES256

Server Random = ABC456

Now both sides agree on:

TLS Version
Encryption Algorithm


Step 4 – Server Sends Certificate
----------------------------------
The server now proves its identity.

It sends:
-------------
server.crt

Inside the certificate:
-------------------------
Domain Name

Public Key

Issuer

Validity

Digital Signature

Example:
------
Subject

myapp.company.com

Issuer

Let's Encrypt

Step 5 – Browser Validates the Certificate
-----------------------------------------------
The browser checks:

Is the certificate expired?
YES / NO


Is the domain correct?
Certificate

↓

myapp.company.com

↓

User opened

myapp.company.com

↓

Match


Is the certificate signed by a trusted CA?

The browser contains trusted CA certificates.

Example:

Let's Encrypt

DigiCert

GlobalSign

Amazon Trust Services

If signed by one of these:

Certificate Trusted

Otherwise:

Your connection is not private

This is the warning you see in browsers.



Step 6 – Key Exchange
-------------------------
After trusting the server, the browser and server generate a shared session key.

In modern TLS (1.3), this is typically done using:

ECDHE

(Elliptic Curve Diffie-Hellman Ephemeral)

Important:

The session key is never sent over the network.

Instead:

Browser

↓

Math

↓

Server

↓

Math

↓

Both independently generate

THE SAME SESSION KEY

Even if someone captures the packets, they cannot derive the session key.


Step 7 – Secure Communication Starts
-----------------------------------
Both now have:

Session Key

All application data is encrypted.

Example:

GET /login

↓

Encrypted

↓

Server

Response:

HTTP/1.1 200 OK

↓

Encrypted

↓

Browser

No one can read the data without the session key.

Complete TLS 1.3 Flow
----------------------
Client (Browser)
        │
        ▼
   Client Hello
        │
        ▼
Server Hello
Certificate
Key Share
        │
        ▼
Certificate Validation
        │
        ▼
Generate Shared Session Key
        │
        ▼
Encrypted Communication


Where Does This Happen in Your EKS Architecture?
-------------------------------------------------
Suppose you've implemented:

Route53
cert-manager
Let's Encrypt
NGINX Ingress
Spring Boot Application

Flow:

User Browser
      │
      ▼
DNS (Route53)
      │
      ▼
AWS ALB
      │
HTTPS (TLS Handshake)
      ▼
NGINX Ingress
      │
HTTP or HTTPS (depending on your design)
      ▼
Spring Boot Service
      │
      ▼
Spring Boot Pod

If you're using end-to-end TLS, then another TLS handshake occurs between:

NGINX Ingress

↓

Spring Boot Service

TLS 1.2 vs TLS 1.3
------------------

| Feature         | TLS 1.2          | TLS 1.3           |
| --------------- | ---------------- | ----------------- |
| Handshake       | More round trips | Fewer round trips |
| Performance     | Slower           | Faster            |
| Security        | Good             | Better            |
| Old ciphers     | Supported        | Removed           |
| Forward Secrecy | Optional         | Mandatory         |
