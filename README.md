# **AWS Certificate Manager (ACM)**
- AWS Certificate Manager (ACM) handles the complexity of creating, storing, and renewing public and private SSL/TLS X.509 certificates and keys that protect your AWS websites and applications. You can provide certificates for your integrated AWS services either by issuing them directly with ACM or by importing third-party certificates into the ACM management system. ACM certificates can secure singular domain names, multiple specific domain names, wildcard domains, or combinations of these. ACM wildcard certificates can protect an unlimited number of subdomains. You can also export ACM certificates signed by AWS Private CA for use anywhere in your internal PKI.
- ACM is used to provision, manage, and deploy **SSL/TLS certificates** for securing websites and applications.

### **Features of ACM**
1. **Automatic Certificate Management** – AWS renews certificates automatically.
2. **Integration with AWS Services** – Works with ELB, CloudFront, API Gateway, etc.
3. **Free Public Certificates** – ACM provides free SSL/TLS certificates.
4. **Private Certificate Issuance** – Issues private certificates via AWS Private CA.
5. **Certificate Import** – Supports importing third-party certificates.

---

### **How to Configure ACM**

<details>
  <summary>Steps to Create ACM</summary>

#### **Step 1: Request a Certificate**
1. Open **ACM Console** → Click **Request a Certificate**.
2. Choose **Public Certificate** (for internet-facing apps).
3. Enter your **domain name** (e.g., `example.com`).
4. Click **Next**.

#### **Step 2: Validate the Certificate**
ACM offers two validation methods:
1. **DNS Validation (Recommended)**
   - ACM provides CNAME records.
   - Add them in **Route 53** (or other DNS providers).
   - Wait for ACM to issue the certificate.
2. **Email Validation**
   - ACM sends emails to domain contacts.
   - Click the approval link.

#### **Step 3: Deploy the Certificate**
- Use ACM certificates in:
  1. **CloudFront** – Secure content delivery.
  2. **ELB** – Secure traffic to EC2 instances.
  3. **API Gateway** – Secure API endpoints.

#### **Step 4: Monitor and Renew**
- ACM automatically renews public certificates.
- Check **Certificate Status** in ACM Console.

</details>

---

### AWS Certificate Manager Concepts

**ACM Certificate**  
An ACM certificate is an X.509 certificate that is valid for 13 months (395 days) and includes various extensions like Key Usage, Extended Key Usage, and CRL Distribution Points.

**ACM Root CAs**  
Certificates issued by ACM derive their trust from Amazon’s Root Certificate Authorities (CAs), including Amazon Root CA 1, 2, 3, and 4, with varying encryption strengths (RSA and Elliptic Curve).

**Apex Domain**  
The main domain name (e.g., example.com), excluding subdomains like www.

**Asymmetric Key Cryptography**  
This involves a pair of keys: one public and one private. The public key is shared, while the private key remains secure.

**Certificate Authority (CA)**  
An entity that issues digital certificates, confirming the identity of the subject and binding it to the public key.

**Certificate Transparency Logging**  
A system to log SSL/TLS certificates issued for your domain to ensure they are authorized, helping prevent fraudulent certificates.

**Domain Name System (DNS)**  
A hierarchical system used to translate domain names (like aws.amazon.com) into IP addresses.

**Domain Names**  
Text strings (e.g., www.example.com) that represent IP addresses. A domain name includes labels like TLD (e.g., .com) and subdomains.

**Encryption and Decryption**  
Encryption secures data, while decryption reverses this process. It uses algorithms and keys, with public or private keys for encryption/decryption.

**Fully Qualified Domain Name (FQDN)**  
The complete DNS name, including the domain and TLD (e.g., aws.amazon.com).

**Public Key Infrastructure (PKI)**  
A framework for managing digital certificates, including creation, distribution, and revocation.

**Root Certificate**  
The top-level certificate in a CA hierarchy. It is self-signed and trusted by browsers.

**Secure Sockets Layer (SSL)**  
A cryptographic protocol (replaced by TLS) that ensures secure communication over the internet using certificates.

**Secure HTTPS**  
An encrypted version of HTTP using SSL/TLS to secure data between the server and client.

**SSL Server Certificates**  
Certificates used to authenticate a server in HTTPS transactions, ensuring the server’s identity.

**Symmetric Key Cryptography**  
Uses the same key for both encryption and decryption, unlike asymmetric cryptography.

**Transport Layer Security (TLS)**  
The successor to SSL, used to secure data between clients and servers.

**Trust**  
Browsers trust websites based on valid certificates issued by trusted CAs. When a certificate is verified, the browser displays a secure lock icon.

---

