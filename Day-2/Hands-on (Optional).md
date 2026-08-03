If you have OpenSSL installed, you can explore these concepts:
==============================================================


# Generate an RSA private key
openssl genrsa -out private.key 2048

# Extract the corresponding public key
openssl rsa -in private.key -pubout -out public.key

# Create a SHA-256 hash of a file
echo "Hello TLS" > message.txt
openssl dgst -sha256 message.txt

# Sign the file using the private key
openssl dgst -sha256 -sign private.key -out signature.bin message.txt

# Verify the signature using the public key
openssl dgst -sha256 -verify public.key -signature signature.bin message.txt
