---
name: code-review
description: "Analyze code quality, security vulnerabilities, performance issues, and best practices. Use when reviewing code, performing security audits, or identifying bugs and improvements."
---

# Code Review Skill

Comprehensive code analysis focusing on quality, security, performance, and best practices.

## When to Use

Use this skill when the user wants to:
- Review code for bugs and logical errors
- Identify security vulnerabilities
- Evaluate code quality and maintainability
- Optimize performance
- Check adherence to best practices
- Generate code quality reports

## Review Areas

### Security
- **Injection Attacks**: SQL injection, Command injection, LDAP injection.
- **Broken Authentication**: Weak password policies, insecure session management, JWT misconfigurations.
- **Sensitive Data Exposure**: Logging secrets, transmitting unencrypted data, improper error messages.
- **Cross-Site Scripting (XSS)**: Unsanitized user input in HTML/JavaScript.
- **Cross-Site Request Forgery (CSRF)**: Lack of anti-CSRF tokens.
- **Insecure Deserialization**: Untrusted data used to instantiate objects.
- **Broken Access Control**: IDOR (Insecure Direct Object Reference), privilege escalation.
- **Dependency Vulnerabilities**: Using outdated or compromised libraries.

### Code Quality
- **Complexity**: High cyclomatic complexity, deeply nested loops/conditionals.
- **Modularity**: Violation of Single Responsibility Principle (SRP), overly large classes/functions.
- **Naming**: Non-descriptive or inconsistent variable/function names.
- **DRY (Don't Repeat Yourself)**: Redundant code blocks that should be abstracted.
- **Error Handling**: Swallowing exceptions, insufficient logging, improper error response codes.
- **Testing Coverage**: Missing unit/integration tests for critical logic paths.

### Performance
- **Complexity Analysis**: Suboptimal time/space complexity (e.g., $O(n^2)$ where $O(n)$ is possible).
- **Resource Leaks**: Unclosed database connections, file handles, or memory leaks.
- **Database Efficiency**: N+1 query problems, missing indexes, unnecessary large joins.
- **Concurrency Issues**: Race conditions, deadlocks, improper use of async/await.
- **Caching**: Missing opportunities for caching frequently accessed data.

### Maintainability
- **Documentation**: Missing or outdated comments and READMEs.
- **Consistency**: Deviation from project coding standards and style guides.
- **Readability**: Code that is difficult to follow due to "clever" but obscure logic.

## Review Workflow

1.  **Preparation**: Understand the context, requirements, and scope of the changes.
2.  **Static Analysis**: Run linters, security scanners (SAST), and check for style consistency.
3.  **Logic & Security Audit**: Manually trace critical paths, checking for edge cases and vulnerabilities.
4.  **Performance Check**: Identify potential bottlenecks and resource-intensive operations.
5.  **Feedback Generation**: Document findings with clear descriptions, severity levels, and suggested fixes.
6.  **Follow-up**: Verify that identified issues have been addressed in the subsequent revision.

## Deliverables

- **Code Review Report**: A detailed summary of findings.
- **Severity Classification**: Issues categorized as Critical, High, Medium, or Low.
- **Actionable Recommendations**: Specific suggestions accompanied by code examples.
- **Refactored Code Snippets**: Examples of how to implement the suggested changes.
- **Priority List**: A ranked list of items to address based on severity and impact.

## Common Mistakes to Avoid

- **Nitpicking**: Focusing too much on trivial style issues instead of logic/security.
- **Being Vague**: Saying "this is bad" instead of explaining *why* and *how* to fix it.
- **Ignoring Context**: Applying rules blindly without considering the specific use case.
- **Over-engineering**: Suggesting overly complex solutions for simple problems.

## Quality Checklist

- [ ] Security vulnerabilities (Injection, XSS, etc.) are identified.
- [ ] Logic errors and edge cases are checked.
- [ ] Performance bottlenecks and resource leaks are addressed.
- [ ] Code is modular, readable, and follows DRY principles.
- [ ] Error handling is robust and informative.
- [ ] Testing coverage is sufficient for the changes.
- [ ] Documentation is updated to reflect changes.
