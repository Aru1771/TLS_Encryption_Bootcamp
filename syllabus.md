TLS Bootcamp (Complete Roadmap)
================================

Phase 1: TLS Fundamentals (Networking)

Day 1 – Why TLS Exists (Today)
-------------------------------
What is encryption?
Symmetric vs Asymmetric encryption
Why HTTP is insecure
Why HTTPS is secure
What is SSL?
Why SSL became TLS
TLS terminology
Public Key
Private Key
Certificates
Certificate Authority (CA)
Root CA
Intermediate CA
Self-signed certificates
Trust chain
How browsers trust websites

Hands-on

Generate your first key pair with OpenSSL.
Create your first self-signed certificate.
Inspect certificates.


Day 2 – TLS Handshake
----------------------
What happens when opening https://google.com
TLS 1.2 handshake
TLS 1.3 handshake
Session keys
Digital signatures
Cipher suites
Certificate validation
SNI (Server Name Indication)
ALPN
Perfect Forward Secrecy

Hands-on

Use openssl s_client
Inspect live certificates
Decode a certificate



Day 3 – PKI (Public Key Infrastructure)
----------------------------------------
Root CA
Intermediate CA
Certificate lifecycle
CSR (Certificate Signing Request)
Certificate issuance
Certificate revocation
CRL
OCSP

Hands-on

Build your own CA
Sign your own server certificate
Verify trust chains


Phase 2: TLS in Linux & Servers
-----------------------------------
Day 4
-------
TLS in Nginx
TLS in Apache
TLS in HAProxy
TLS in Envoy
HTTPS virtual hosts

Hands-on

Configure HTTPS in Nginx



Day 5
-----
Mutual TLS (mTLS)
Client certificates
API authentication with certificates
TLS debugging
Common certificate errors

Hands-on

Nginx mTLS lab


Phase 3: TLS in Kubernetes
---------------------------
Day 6
-----
Kubernetes PKI architecture
Cluster CA
API Server certificates
etcd certificates
Kubelet certificates
Controller certificates
Scheduler certificates

Hands-on

Explore /etc/kubernetes/pki


Day 7
------
Kubernetes authentication using certificates
kubeconfig certificates
Client certificates
Certificate rotation

Hands-on

Generate a Kubernetes user certificate


Day 8
------
TLS inside Ingress
cert-manager
ClusterIssuer
Issuer
Let's Encrypt
ACME challenge

Hands-on

Deploy cert-manager
Issue a real certificate

Day 9
------
Internal mTLS
Istio mTLS
Linkerd mTLS
Service Mesh


Day 10
------
TLS troubleshooting
Expired certificates
Wrong SAN
x509 errors
Production interview scenarios

Phase 4: Cloud TLS
-------------------

Day 11
-------
AWS ACM
ACM Private CA
ALB HTTPS
NLB TLS
CloudFront HTTPS
Route 53 validation

Day 12
------
EKS TLS
IAM Authenticator
IRSA trust
OIDC certificates
Phase 5: Production & Interviews

Day 13
--------
Real production architectures
Certificate renewal
Secret management
Vault PKI
cert-manager production setup

Day 14
-----
100+ Interview Questions
Troubleshooting labs
Mock interview
Real-world scenarios
Bootcamp Rules

For each day we'll follow the same structure:
----------------------------------------------
Theory – Understand the concepts from first principles.
Architecture diagrams – Visualize how components interact.
Hands-on labs – Use OpenSSL, Linux, Docker, Kubernetes, or AWS.
Interview questions – Practice explaining the concepts clearly.
Production scenarios – Learn how these concepts are used in real environments.

This way, you'll not only know what TLS is, but also why it works, how it's implemented, and how to troubleshoot it in production.
