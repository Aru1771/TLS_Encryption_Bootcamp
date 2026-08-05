Certificates, Certificate Authorities (CA), PKI
==============================================

First Question
----------------
Why do we need certificates?

Suppose you type:

https://amazon.com

How do you know you're really talking to Amazon?

What if a hacker creates a fake website?

amazon.com  ❌

amazan.com  ❌

amaz0n.com  ❌

How can your browser verify the real website?


What is a Digital Certificate?
--------------------------------

Think of it as an ID card for a website.

Example:

Website

amazon.com

Identity Card

↓

Digital Certificate

Just like your Aadhaar card proves your identity,

a digital certificate proves the website's identity.

What information does a certificate contain?
-------------------------------------------------

A certificate contains:

Website Name

amazon.com

-------------------

Public Key

ABC123XYZ...

-------------------

Issued By

Amazon Trust Services

-------------------

Valid From

Jan 1

-------------------

Valid Until

Jan 1 Next Year

-------------------

Digital Signature

👉 Answer: Using a Digital Certificate.


Remember:

The certificate contains the Public Key.

The Private Key never leaves the server.


Public Key vs Private Key
--------------------------
Imagine a mailbox.

Everyone can put letters into it.

Only the owner can open it.

Everyone

↓

Public Key

↓

Encrypted Data

↓

Private Key

↓

Original Data

Public Key:
-----------
Shared with everyone
Used for encryption or signature verification

Private Key:
------------
Secret
Stored securely on the server
Used for decryption or creating digital signatures

Who issues certificates?
-------------------------

Can anyone create a certificate?

Yes.

Will browsers trust it?

❌ No.

Certificates must be issued by a trusted organization called a Certificate Authority (CA).

Examples:

DigiCert
Let's Encrypt
GlobalSign
Sectigo

What is a Certificate Authority (CA)?
--------------------------------------
A CA is a trusted organization that verifies the website owner's identity before issuing a certificate.

Think of it like a passport office.

Passport Office

↓

Verifies You

↓

Issues Passport

Similarly,

Certificate Authority

↓

Verifies Website

↓

Issues Certificate

Why do browsers trust the CA?
------------------------------

Browsers already contain a list of trusted CA certificates.

Chrome

↓

Trusted CA List

↓

DigiCert

Let's Encrypt

GlobalSign


If the website certificate is signed by one of these trusted CAs, the browser accepts it.

What is PKI (Public Key Infrastructure)?
-----------------------------------------

PKI is the complete system that manages certificates.

It includes:

Certificate Authority

↓

Certificates

↓

Public Keys

↓

Private Keys

↓

Certificate Revocation

↓

Trust

Think of PKI as the entire ecosystem behind digital certificates.


Certificate Chain
-------------------
A website certificate is usually not signed directly by the Root CA.

Instead:

Root CA

↓

Intermediate CA

↓

Website Certificate

Example:

Root CA

↓

Amazon Trust Services

↓

amazon.com

Why Intermediate CAs?
--------------------------
Reasons:

Better security
Easier certificate management
Protect the Root CA

If an Intermediate CA is compromised, it can be replaced without replacing the Root CA.


How does the browser verify a certificate?
-----------------------------------------------
Example:

You visit

amazon.com

↓

Server sends certificate

↓

Browser checks:

1. Is it expired?

2. Is the domain correct?

3. Was it signed by a trusted CA?

4. Is the signature valid?

↓

Yes

↓

HTTPS connection continues

If any check fails:

Your connection is not private


Self-Signed Certificate
-------------------------
Anyone can create one.

Example:

openssl req -x509

But browsers don't trust it by default.

Used for:

Development
Testing
Internal servers

Not recommended for public websites.

Connection
🎯 Interview Questions (Day 2
-----------------------------
Q1. What is a digital certificate?

It is a digital identity document that proves a website's identity and contains its public key.

Q2. What is a CA?

A trusted organization that verifies website ownership and issues certificates.

Q3. What is PKI?

The complete system of certificates, public/private keys, certificate authorities, and trust management.

Q4. What is the difference between a Public Key and a Private Key?
| Public Key                      | Private Key       |
| ------------------------------- | ----------------- |
| Shared publicly                 | Kept secret       |
| Encrypts or verifies signatures | Decrypts or signs |

Q5. What is a Certificate Chain?

A chain of trust:

Root CA

↓

Intermediate CA

↓

Website Certificate
