Module 2: Cryptography Fundamentals
===================================

Before we understand TLS Handshake, we need to understand the cryptographic building blocks that TLS uses.

TLS is not a single algorithm.

It is a combination of multiple cryptographic techniques working together.

Today's goal is to understand:

Symmetric Encryption
Asymmetric Encryption
Hashing
Digital Signatures

These four concepts are the foundation of TLS.


Part 1 – Symmetric Encryption
-----------------------------

Imagine you have a secret box.

You lock it with a key.

Your friend opens it using the same key.

Message
   │
Encrypt using Secret Key
   │
Ciphertext
   │
Internet
   │
Decrypt using SAME Secret Key
   │
Original Message

Both sender and receiver use one identical key.

Example:
---------
Secret Key: MySecret123

Sender encrypts: Hello Amazon

Ciphertext becomes: G@7L!Q#92Lm

Receiver uses: MySecret123

to decrypt it back.


Real-Life Example
-----------------

Think of a locker.

You and your friend both have duplicate copies of the same locker key.

One locks.

The other unlocks.

Exactly the same concept.

Advantages:
-----------
Very fast
Low CPU usage
Suitable for encrypting large amounts of data

Examples:

AES
ChaCha20

Modern TLS uses these algorithms to encrypt application data after the handshake.

Biggest Problem
---------------

How do both parties get the same secret key securely?

Suppose Amazon wants to use:

SecretKey = ABC123

How does Amazon send this key to your browser securely?

If the key travels over the Internet in plain text:

ABC123

An attacker can steal it.

Now the attacker has the key.

This is called the Key Distribution Problem.

This is exactly the problem we discussed at the end of Day 1.



