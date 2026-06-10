---
name: security-audit
description: "Perform security assessments, vulnerability scanning, and penetration testing for codebases, APIs, and infrastructure. Use when conducting security reviews, penetration tests, or compliance assessments."
---

# Security Audit Skill

Comprehensive security assessment and vulnerability detection for applications and systems.

## When to Use

Use this skill when the user wants to:
- Conduct security code reviews
- Perform penetration testing
- Scan for known vulnerabilities
- Evaluate security posture
- Check compliance requirements (e.g., GDPR, HIPAA, PCI DSS)
- Identify data protection issues

## Audit Scope

### Application Security (OWASP Top 10 Focus)
- **Broken Access Control**: Insecure direct object references (IDOR), privilege escalation.
- **Cryptographic Failures**: Weak algorithms, hardcoded secrets, improper key management.
- **Injection**: SQL injection, Command injection, LDAP/NoSQL injection.
- **Insecure Design**: Flaws in business logic and architectural design.
- **Security Misconfiguration**: Default passwords, unnecessary features enabled, verbose error messages.
- **Vulnerable and Outdated Components**: Using libraries with known vulnerabilities (CVEs).
- **Identification and Authentication Failures**: Weak password policies, session fixation, lack of MFA.
- **Software and Data Integrity Failures**: Insecure deserialization, untrusted updates.
- **Security Logging and Monitoring Failures**: Insufficient logging to detect/respond to breaches.
- **Server-Side Request Forgery (SSRF)**: Forcing the server to make unauthorized requests.

### Infrastructure Security
- **Network Configurations**: Open ports, insecure protocols (Telnet, FTP), lack of segmentation.
- **Container/VM Hardening**: Running as root, unpatched OS, unnecessary services.
- **Configuration Management**: Drift from secure baseline configurations.
- **Secrets Management**: Unprotected API keys, certificates, or credentials in code/config.

### Data Security
- **Data at Rest Encryption**: Lack of encryption for databases and backups.
- **Data in Transit Encryption**: Using HTTP instead of HTTPS, weak TLS versions.
- **PII/PHI Handling**: Improper storage or transmission of sensitive user data.
- **Data Breach Response**: Absence of incident response plans.

## Audit Tools

- **Dynamic Analysis (DAST)**: Burp Suite, OWASP ZAP.
- **Static Analysis (SAST)**: SonarQube, Bandit, Snyk, Semgrep.
- **Dependency Scanning (SCA)**: Dependabot, Snyk, OWASP Dependency-Check.
- **Network Scanning**: Nmap, Nessus.

## Deliverables

- **Executive Summary**: High-level overview of the security posture and risk rating.
- **Detailed Vulnerability Findings**: Descriptions, impact, and technical details.
- **Remediation Recommendations**: Clear guidance on how to fix each issue with code examples.
- **Priority-ordered Action Items**: Ranked by severity (Critical, High, Medium, Low).
- **Compliance Checklist**: Verification against specific standards (if requested).
- **Proof-of-Concept (PoC)**: Demonstrations of vulnerabilities (only if authorized).

## Common Pitfalls in Auditing

- **Ignoring the "Human" Element**: Forgetting to check for social engineering or process weaknesses.
- **Scope Creep**: Testing systems outside the agreed-upon boundaries.
- **False Positives**: Reporting non-issues as vulnerabilities without verification.
- **Lack of Remediation Guidance**: Identifying problems but not explaining how to fix them.

## Quality Checklist

- [ ] All high and critical vulnerabilities are addressed.
- [ ] Remediation steps are clear, actionable, and include code examples.
- [ ] Risk rating is justified with impact/likelihood analysis.
- [ ] Compliance requirements (if any) are met.
- [ ] Report is well-structured, readable, and professional.
- [ ] Evidence (screenshots, logs, code snippets) is provided for each finding.
