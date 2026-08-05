TLS Versions, Cipher Suites & Record Protocol
---------------------------------------------

What happens after the browser trusts the certificate?

Now the client and server need to communicate securely.

They decide:

Which TLS version to use
Which encryption algorithm to use
Which integrity algorithm to use

This is done using a Cipher Suite.

What is a Cipher Suite?
-------------------------

Think of it as a security package.

Example:

TLS_AES_256_GCM_SHA384

This tells both client and server exactly how to communicate securely.

Breaking it down
-------------------

TLS

↓

AES-256

↓

GCM

↓

SHA384

AES-256
-----------
Used for:

Encryption

Purpose:

Hide the data.

GCM
----
Used for:

Authentication and Integrity

Purpose:

Detect if data was modified.


SHA-384
--------
Used in the handshake for cryptographic operations such as HKDF in TLS 1.3 and related integrity functions.

TLS Versions
| Version | Status              |
| ------- | ------------------- |
| SSL 2.0 | ❌ Insecure          |
| SSL 3.0 | ❌ Insecure          |
| TLS 1.0 | ❌ Deprecated        |
| TLS 1.1 | ❌ Deprecated        |
| TLS 1.2 | ✅ Still widely used |
| TLS 1.3 | ✅ Recommended       |


Why TLS 1.3?
---------------
Advantages:

Faster handshake
Stronger security
Fewer insecure algorithms
Perfect Forward Secrecy is mandatory
