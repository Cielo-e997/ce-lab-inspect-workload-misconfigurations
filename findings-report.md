# Security Misconfiguration Lab Report

## Misconfigurations Identified

### Misconfiguration 1: Public S3 Bucket
- **Threat:** Information Disclosure (STRIDE: I)
- **Risk Level:** Critical
- **Impact:** Customer PII exposed to internet
- **Detection:** AWS Config rule s3-bucket-public-read-prohibited

### Misconfiguration 2: SSH Open to Internet
- **Threat:** Unauthorized Access (STRIDE: S - Spoofing)
- **Risk Level:** Critical
- **Impact:** Brute force attacks, potential instance compromise
- **Detection:** AWS Config rule restricted-ssh

### Misconfiguration 3: Overly Permissive IAM Role
- **Threat:** Elevation of Privilege (STRIDE: E)
- **Risk Level:** Critical
- **Impact:** Compromised application can access all AWS resources
- **Detection:** IAM Access Analyzer, manual review

---

## Misconfigurations Summary

| # | Misconfiguration | Risk Level | Remediation | Status |
|---|------------------|------------|-------------|--------|
| 1 | Public S3 bucket | Critical | Enable Block Public Access, encryption | ✅ Fixed |
| 2 | SSH open to 0.0.0.0/0 | Critical | Restrict to corporate VPN | ✅ Fixed |
| 3 | IAM AdministratorAccess | Critical | Apply least privilege | ✅ Fixed |

## Detection Methods
- AWS Config rules (automated)
- Manual review (IAM policies)

## Lessons Learned
1. Default-deny is critical (Block Public Access)
2. Regular Config rule evaluation catches misconfigurations
3. IAM Access Analyzer should be enabled for ongoing monitoring

## Recommendations
1. Enable Security Hub for centralized findings
2. Implement infrastructure as code to enforce secure baselines
3. Conduct quarterly security reviews