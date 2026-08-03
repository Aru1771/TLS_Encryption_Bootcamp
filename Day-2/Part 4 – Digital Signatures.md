Part 4 – Digital Signatures
===========================

So far we know:

Encryption provides confidentiality.

Hashing helps detect changes.

But how do we know who actually sent the message?

That's where digital signatures come in.

Suppose Amazon sends:
----------------------
Payment Approved

Amazon first calculates a hash.

Message

↓

SHA-256

↓

Hash

Then Amazon encrypts that hash using its private key.

This encrypted hash is called the digital signature.

The server sends:

Message

+

Digital Signature

The browser receives both.
-----------------------------
It:

Calculates the hash of the received message.
Decrypts the digital signature using Amazon's public key.
Compares the two hashes.
If they match:
----------
The message wasn't modified (Integrity).
The sender possessed Amazon's private key (Authentication).

If they don't match, the message is rejected.

If they match:

The message wasn't modified (Integrity).
The sender possessed Amazon's private key (Authentication).

If they don't match, the message is rejected.

Summary:
---------
| Technique             | Purpose                          | Reversible?                      | Key Used?                                 |
| --------------------- | -------------------------------- | -------------------------------- | ----------------------------------------- |
| Symmetric Encryption  | Confidentiality                  | ✅ Yes                            | One shared secret key                     |
| Asymmetric Encryption | Secure key exchange & encryption | ✅ Yes                            | Public & Private keys                     |
| Hashing               | Integrity                        | ❌ No                             | No key                                    |
| Digital Signature     | Authentication & Integrity       | Signature verified, not reversed | Private key to sign, Public key to verify |
