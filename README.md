# **AWS Certificate Manager (ACM)**
- AWS Certificate Manager (ACM) handles the complexity of creating, storing, and renewing public and private SSL/TLS X.509 certificates and keys that protect your AWS websites and applications. You can provide certificates for your integrated AWS services either by issuing them directly with ACM or by importing third-party certificates into the ACM management system. ACM certificates can secure singular domain names, multiple specific domain names, wildcard domains, or combinations of these. ACM wildcard certificates can protect an unlimited number of subdomains. You can also export ACM certificates signed by AWS Private CA for use anywhere in your internal PKI.
- ACM is used to provision, manage, and deploy **SSL/TLS certificates** for securing websites and applications.

### **Features of ACM**
1. **Automatic Certificate Management** – AWS renews certificates automatically.
2. **Integration with AWS Services** – Works with ELB, CloudFront, API Gateway, etc.
3. **Free Public Certificates** – ACM provides free SSL/TLS certificates.
4. **Private Certificate Issuance** – Issues private certificates via AWS Private CA.
5. **Certificate Import** – Supports importing third-party certificates.

### What is the right AWS certificate service for my needs?
**1. **AWS Certificate Manager (ACM)****
- This service is for enterprise customers who need a secure web presence using TLS. ACM certificates are deployed through Elastic Load Balancing, Amazon CloudFront, Amazon API Gateway, and other integrated AWS services. The most common application of this kind is a secure public website with significant traffic requirements. ACM also simplifies security management by automating the renewal of expiring certificates. You are in the right place for this service.

**2. **AWS Private CA****
- This service is for enterprise customers building a public key infrastructure (PKI) inside the AWS cloud and intended for private use within an organization. With AWS Private CA, you can create your own certificate authority (CA) hierarchy and issue certificates with it for authenticating users, computers, applications, services, servers, and other devices. Certificates issued by a private CA cannot be used on the internet. For more information, see the AWS Private CA User Guide.
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

### **ACM Certificate Integration with AWS Services**

1. **Elastic Load Balancing (ELB)**  
   ELB distributes traffic across EC2 instances and automatically scales. ACM certificates can be deployed on the load balancer for SSL/TLS encryption.  
   *For details, see the Elastic Load Balancing User Guide.*

2. **Amazon CloudFront**  
   CloudFront speeds up content delivery globally. ACM certificates can secure CloudFront distributions for SSL/TLS.  
   *Request certificates in the US East (N. Virginia) region.*

3. **Amazon Cognito**  
   ACM certificates are used for custom domains with CloudFront proxies in Cognito user pools.  
   *Certificates are managed automatically, but must be disassociated before deletion.*

4. **AWS Elastic Beanstalk**  
   Beanstalk uses ELB for load balancing and can deploy ACM certificates for HTTPS termination.  
   *See the Elastic Beanstalk Developer Guide for more.*

5. **AWS App Runner**  
   App Runner automates certificate management for custom domains, storing certificates in ACM.  
   *Certificates remain for seven days post-service/domain removal.*

6. **Amazon API Gateway**  
   ACM certificates are used for custom domain names to secure APIs.  
   *See the API Gateway Developer Guide for more.*

7. **AWS Nitro Enclaves**  
   Nitro Enclaves allow isolated environments in EC2. ACM certificates can be used with Nitro-connected instances.  
   *See AWS Certificate Manager for Nitro Enclaves.*

8. **AWS CloudFormation**  
   CloudFormation automates resource setup, including ACM certificates, for secure connections.  
   *Ensure proper validation during stack creation to avoid delays.*

9. **AWS Amplify**  
   Amplify automatically generates ACM certificates when you connect a custom domain to your application.

10. **Amazon OpenSearch Service**  
    ACM certificates secure the Application Load Balancer for OpenSearch clusters with custom domains.

11. **AWS Network Firewall**  
    Network Firewall integrates with ACM for TLS inspection, using certificates for decryption and re-encryption of SSL/TLS traffic.  
    *See the AWS Network Firewall Developer Guide for setup details.*

---

### **AWS Certificate Manager (ACM) Security Overview**

**Cloud Security at AWS**  
AWS prioritizes security, with data centers and architectures built for highly sensitive requirements. Cloud security is a shared responsibility between AWS and the customer, outlined as:

- **Security of the Cloud**: AWS protects the infrastructure and provides secure services, regularly audited for compliance.
- **Security in the Cloud**: The customer is responsible for configuring services securely, based on the specific AWS service used, data sensitivity, and applicable laws.

**Using ACM Securely**  
Helps you implement the shared responsibility model when using AWS Certificate Manager (ACM) to meet your security and compliance needs. Key areas include:

- **Data Protection**: Ensuring the confidentiality and integrity of data managed by ACM.
- **Identity and Access Management (IAM)**: Controlling access to ACM resources.
- **Resilience**: Configuring ACM for high availability and disaster recovery.
- **Infrastructure Security**: Understanding ACM’s security features and best practices for secure operations.

---

### **Managed Certificate Renewal in AWS Certificate Manager**

AWS Certificate Manager (ACM) automates SSL/TLS certificate renewal for Amazon-issued certificates. This includes automatic renewals for DNS-validated certificates and email notifications for other certificates nearing expiration. This applies to both public and private ACM certificates.

**Eligibility Criteria for Automatic Renewal:**

- **Eligible:**
  - Associated with AWS services like Elastic Load Balancing or CloudFront.
  - Exported since issuance or last renewal.
  - Private certificates issued via ACM API, exported, or associated with AWS services.
  - Private certificates issued via the management console, then exported or associated with AWS services.

- **Not Eligible:**
  - Private certificates issued via the AWS Private CA IssueCertificate API.
  - Imported certificates.
  - Expired certificates.

**Punycode and Internationalized Domain Name (IDN) Requirements:**

- Domain names starting with "<character><character>--" must match "xn--."
- Domain names starting with "xn--" must be valid IDNs.

**Punycode Examples:**

| Domain Name        | Fulfills #1 | Fulfills #2 | Valid? | Notes                             |
|--------------------|--------------|--------------|--------|-----------------------------------|
| example.com        | n/a          | n/a          | ✓      | Does not start with "<character><character>--" |
| a--example.com     | n/a          | n/a          | ✓      | Does not start with "<character><character>--" |
| abc--example.com   | n/a          | n/a          | ✓      | Does not start with "<character><character>--" |
| xn--xyz.com        | Yes          | Yes          | ✓      | Valid IDN (resolves to 简.com)   |
| xn--example.com    | Yes          | No           | ✗      | Invalid IDN                      |
| ab--example.com    | No           | No           | ✗      | Must start with "xn--"            |

**Certificate Renewal Details:**

- ARN remains the same after renewal.
- ACM certificates are regional resources, so certificates in different AWS Regions must be renewed separately.

---
