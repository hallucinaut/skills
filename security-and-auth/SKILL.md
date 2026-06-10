---
name: security-and-auth
description: "Implement authentication, authorization, and security auditing. Protect applications against common vulnerabilities and ensure data integrity through validation."
---

# Security and Authentication Skill

Secure applications by implementing robust identity management, access controls, and proactive security measures.

## When to Use

Use this skill when the user wants to:
- Implement authentication (Login, Register, OAuth, JWT, Sessions)
- Implement authorization (RBAC, ABAC, Permission-based)
- Perform security auditing and vulnerability assessments
- Implement request/response validation to prevent injection attacks
- Secure an application against OWASP Top 10 vulnerabilities

## Core Concepts

### 1. Authentication (AuthN)
- **Goal**: Verify the identity of a user or service.
- **Methods**:
    - **Passwords**: Hashed and salted (e.g., Argon2, bcrypt).
    - **Tokens**: Stateless (JWT) or State-based (Session Cookies).
    - **Social/External**: OAuth 2.0, OpenID Connect (Google, GitHub, etc.).
    - **Multi-Factor Authentication (MFA)**: Adding an extra layer of security.

### 2. Authorization (AuthZ)
- **Goal**: Determine what an authenticated user is allowed to do.
- **Models**:
    - **RBAC (Role-Based Access Control)**: Based on user roles (e.g., `Admin`, `Editor`).
    - **ABAC (Attribute-Based Access Control)**: Based on attributes (e.g., `User.Department == Resource.Department`).
    - **ACL (Access Control Lists)**: Fine-grained permissions for specific resources.

### 3. Security Auditing & Defense
- **Input Validation**: Strict schema validation for all incoming data to prevent SQL Injection, XSS, and Command Injection.
- **Security Headers**: Using `Content-Security-Policy` (CSP), `X-Frame-Options`, etc.
- **Rate Limiting**: Preventing brute force and DoS attacks.
- **Audit Logs**: Recording critical security events (logins, permission changes, failed attempts).
- **Secrets Management**: Using environment variables or dedicated vaults (e.g., HashiCorp Vault, AWS Secrets Manager) instead of hardcoding keys.

## Best Practices

### Identity & Access Management
- **Never store plain-text passwords.** Use strong, modern hashing algorithms.
- **Use short-lived access tokens** and longer-lived refresh tokens.
- **Follow the Principle of Least Privilege**: Grant only the minimum necessary permissions.
- **Secure your cookies**: Use `HttpOnly`, `Secure`, and `SameSite` flags.

### Defensive Programming
- **Fail Securely**: If an authentication or authorization check fails, default to denying access.
- **Sanitize everything**: Treat all external input as untrusted.
- **Limit sensitive information in errors**: Don't leak database details or stack traces in production error messages.

### Monitoring & Auditing
- **Log security-critical events**: Successful/failed logins, unauthorized access attempts, privilege escalations.
- **Regularly audit permissions**: Ensure users don't accumulate unnecessary rights (Privilege Creep).

## Deliverables

- Authentication system implementation (Login/Register/OAuth).
- Authorization logic (RBAC/ABAC/ACL).
- Input validation schemas for all sensitive endpoints.
- Security configuration (Headers, Cookies, Rate Limiting).
- Security audit report or checklist.
- Audit logging implementation.

## Quality Checklist

- [ ] Passwords are never stored in plain text and use strong hashing.
- [ ] Authentication is multi-factor aware (if required).
- [ ] Authorization checks are enforced on every sensitive endpoint.
- [ ] All user-provided input is strictly validated against a schema.
- [ ] Sensitive information is not leaked in error messages.
- [ ] Secrets (keys, tokens) are managed via environment variables or vaults.
- [ ] Security headers are configured correctly.
- [ ] Rate limiting is implemented on sensitive endpoints (e.g., login).
