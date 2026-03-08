# Secure Architectures & Encryption Notes

## Identity & Access Management (IAM)
- Use **IAM Roles** for EC2 instances instead of hardcoding API keys.
- **Least Privilege**: Always grant the minimum permissions required for a task.

## Data Encryption at Rest
### S3 Encryption Options
- **SSE-S3**: S3 managed keys (easiest, but less control).
- **SSE-KMS**: AWS Key Management Service (best for auditing and automatic rotation).
- **SSE-C**: Customer-provided keys.
- **CloudTrail**: Essential for auditing *who* accessed *what* key.

## Data Protection
- **S3 Versioning**: Protects against accidental overwrites/deletions.
- **MFA Delete**: Requires a Multi-Factor token to delete objects or change versioning.

> [!IMPORTANT]
> **Exam Tip**: 
> - Need auditing for encryption usage? -> Use **KMS**.
> - Need to prevent accidental deletion? -> Use **Versioning + MFA Delete**.
