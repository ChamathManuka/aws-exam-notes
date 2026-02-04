# AWS Key Management Service (KMS)

## What is AWS KMS?

AWS Key Management Service (KMS) is a **fully managed service** that allows you to:
- Create
- Control
- Rotate
- Use
- Audit cryptographic keys

KMS is used to **encrypt and decrypt data** across AWS services using **envelope encryption**.

AWS KMS integrates natively with many AWS services including:
- Amazon S3 (SSE-KMS)
- Amazon EBS
- Amazon RDS
- Amazon DynamoDB
- Amazon Redshift
- AWS Lambda
- AWS Secrets Manager

---

## Why Organizations Use AWS KMS

### Centralized Key Management
- One place to manage encryption keys
- Consistent encryption policies across services
- No need to build custom key infrastructure

### Strong Security Controls
- Keys never leave AWS KMS unencrypted
- Backed by FIPS 140-2 validated hardware (HSMs)
- Separation of duties:
  - Admins manage keys
  - Applications use keys

### Fine-Grained Access Control
- Controlled via:
  - **KMS Key Policies**
  - IAM policies
  - Grants (temporary permissions)
- Explicit allow required (KMS is deny-by-default)

---

## AWS KMS and Compliance

AWS KMS helps meet **security and regulatory compliance requirements** such as:

- SOC 1, SOC 2
- ISO 27001
- PCI DSS
- HIPAA
- GDPR
- FedRAMP (in supported regions)

### Compliance Benefits
- Encryption at rest and in transit
- Centralized audit logging
- Key lifecycle management
- Customer control over encryption keys

> For regulated industries (finance, healthcare, government), KMS enables **customer-managed encryption**, which is often a compliance requirement.

---

## Auditing and Monitoring (Compliance Critical)

- All KMS API calls are logged in **AWS CloudTrail**
- Logs include:
  - Who used the key
  - When it was used
  - Which service used it
- Enables:
  - Forensics
  - Compliance audits
  - Security investigations

---

## KMS Key Types

### AWS Managed Keys
- Created and managed automatically by AWS
- Limited control
- Used by default in many AWS services
- Example: `aws/s3`, `aws/ebs`

### Customer Managed Keys (CMK)
- Fully controlled by the customer
- Custom key policies
- Manual or automatic rotation
- Required for advanced compliance use cases

### Multi-Region Keys
- Special type of **customer-managed key**
- Identical key material across regions
- Used for cross-region encryption/decryption
- Cannot be converted from single-region keys

---

## Encryption Model Used by KMS

### Envelope Encryption
- Data is encrypted using a **data key**
- Data key is encrypted using a **KMS key**
- Reduces latency and improves scalability
- KMS never directly encrypts large data blobs

---

## S3 Encryption (Minimal Context for KMS)

### SSE-KMS
- Uses AWS KMS Customer Managed Keys
- Provides:
  - Key policies
  - Audit logs
  - Fine-grained access control
- Required when compliance demands customer control

### SSE-S3
- Fully AWS managed
- No customer key visibility
- Simpler but less control

---

## AWS KMS – Multi-Region Keys

### Overview
- Multi-Region Keys (MRKs) are **customer-managed KMS keys** replicated across AWS Regions
- All replicas share:
  - Same key material
  - Same key ID

### Key Benefits
- Encrypt in one region
- Decrypt in another region
- No re-encryption required
- No cross-region KMS calls

### Limitations
- Cannot convert a single-region key to multi-region
- Must be created as multi-region initially
- Key policies are regional and must be managed separately

---

## Exam Summary (High-Yield)

- KMS = centralized encryption + compliance
- Customer-managed keys required for compliance-heavy workloads
- CloudTrail logs all key usage
- Multi-Region Keys enable cross-region decryption
- AWS-managed keys simplify encryption but reduce control

---
