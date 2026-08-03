Part 2 – Asymmetric Encryption
------------------------------

Instead of one key, we now use two mathematically related keys.

Public Key

Private Key

These keys are generated together.

The public key can be shared with everyone.

The private key must always remain secret.

Imagine Amazon publishes:
-------------------------
Public Key

on its website.

Anyone can download it.

But Amazon keeps its

Private Key

inside its server.

Encryption Flow
----------------
Browser

Message
      │
Encrypt using Amazon Public Key
      │
Internet
      │
Amazon Server
      │
Decrypt using Amazon Private Key

Only the private key can decrypt data encrypted with the matching public key.

Why is this Useful?
--------------------

There is no need to send a secret encryption key over the Internet beforehand.

The browser can safely use the server's public key.

Only the server has the corresponding private key.

This solves the key exchange problem conceptually.

Is Asymmetric Encryption Perfect?
----------------------------------
No.

It has one major drawback.

It is much slower than symmetric encryption.

For example:

Encrypting a 1 GB file with RSA would be very slow and CPU intensive.

Even if an attacker intercepts the ciphertext, they cannot decrypt it without the private key.

Why Doesn't TLS Use Only Asymmetric Encryption?
-------------------------------------------------

Imagine watching a 4K movie on Netflix.

Every second, gigabytes of data are transferred.

If all of that were encrypted with RSA or ECC, the servers would be overwhelmed.

So TLS uses a hybrid approach:

Asymmetric cryptography to securely establish shared secrets.
Symmetric cryptography to encrypt the actual data.

This gives both security and performance.
