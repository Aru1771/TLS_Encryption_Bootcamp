Part 3 – Hashing
================

Encryption can be reversed with the correct key.

Hashing is different.

A hash function takes input and produces a fixed-size output.

Hello

↓

SHA-256

↓

185f8db32271fe25...

No key is involved.

And you cannot realistically recover the original message from the hash.


Properties of a Good Hash Function
-------------------------------------
If you change even one character, the hash changes completely.

Example:

Hello

Hash:

ABC123...

Now change it to:

hello

Hash:
XYZ789...

Completely different.

Why is Hashing Important?
-------------------------

Suppose Amazon sends:

Transfer ₹1000

The hash is calculated.

If an attacker changes the message to:

Transfer ₹100000

The new hash is completely different.

The receiver recalculates the hash.

If it doesn't match, the message has been altered.

This helps provide integrity.

Common Hash Algorithms
-----------------------
SHA-256
SHA-384
SHA-512

Older algorithms like MD5 and SHA-1 are considered insecure for modern security purposes.





XYZ789...

Completely different.
