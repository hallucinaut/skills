---
name: software-engineering
description: "Ensure high code quality through testing, linting, debugging, code reviews, and standard Git workflows."
---

# Software Engineering Skill

Maintain high standards of code quality, reliability, and maintainability throughout the development lifecycle.

## When to Use

Use this skill when the user wants to:
- Write unit, integration, and E2E tests.
- Implement linting and static analysis.
- Debug complex application issues.
- Conduct effective code reviews.
- Manage project dependencies.
- Establish Git workflows (e.g., Gitflow, Trunk-based).

## Core Pillars

### 1. Testing & Quality Assurance
- **Unit Testing**: Test individual functions/methods in isolation to ensure they behave correctly.
- **Integration Testing**: Verify that different modules, databases, or services work together seamlessly.
- **End-to-End (E2E) Testing**: Test the entire application flow from the user's perspective to ensure system integrity.
- **Regression Testing**: Ensure new changes don't break existing functionality by running a suite of tests.
- **Test-Driven Development (TDD)**: Write tests before writing code to drive better design and coverage.

### 2. Design Principles & Patterns
- **SOLID Principles**:
    - **S**ingle Responsibility: A class/module should have one reason to change.
    - **O**pen-Closed: Software entities should be open for extension but closed for modification.
    - **L**iskov Substitution: Subtypes must be substitutable for their base types.
    - **I**nterface Segregation: Prefer many client-specific interfaces over one general-purpose interface.
    - **D**ependency Inversion: Depend on abstractions, not concretions.
- **Design Patterns**: Use proven solutions like Singleton, Factory, Observer, Strategy, and Decorator to solve common problems.

### 3. Static Analysis & Linting
- **Linters**: Enforce coding standards and catch syntax errors (e.g., ESLint, Pylint, Flake8).
- **Static Analysis**: Find potential bugs and security vulnerabilities without running the code (e.g., SonarQube, Bandit).
- **Type Checking**: Use static typing to catch type-related errors early (e.g., TypeScript, MyPy, Go).

### 4. Debugging & Troubleshooting
- **Logging**: Implement structured, informative logging for visibility into production systems.
- **Debugging Tools**: Use debuggers, profilers, and tracers to investigate issues.
- **Observability**: Use metrics, logs, and distributed tracing (e.g., Prometheus, Jaeger) to understand system behavior.

### 5. Development Lifecycle & Collaboration
- **Git Workflow**: Use branches, pull requests, and commit conventions (e.g., Conventional Commits) to manage code changes.
- **Code Review**: Review code for logic, readability, security, and adherence to standards.
- **Dependency Management**: Manage third-party libraries using tools like npm, pip, or Maven, ensuring version stability and security scanning.

## Best Practices

- **Test early and often**: Integrate testing into your development loop and CI/CD pipelines.
- **Automate linting and testing**: Don't rely on manual checks; use pre-commit hooks and CI pipelines.
- **Write clean, readable code**: Code is read much more often than it is written. Prioritize clarity over "cleverness."
- **Keep pull requests small**: Small, focused PRs are easier to review and less risky to merge.
- **Treat dependencies as risks**: Regularly audit and update your libraries to avoid security vulnerabilities.
- **Write meaningful commit messages**: Help your future self and teammates understand *why* a change was made.

## Deliverables

- Test suites (Unit, Integration, E2E).
- Linting and static analysis configurations.
- Debugging reports and root cause analysis.
- Code review checklists and processes.
- Dependency manifests and lock files.
- Git workflow documentation.

## Quality Checklist

- [ ] Tests cover core business logic and edge cases.
- [ ] Linting and static analysis are automated in the CI pipeline.
- [ ] Code reviews are thorough and focused on quality.
- [ ] Dependencies are managed and regularly audited.
- [ ] Error logging is informative and actionable.
- [ ] Git history is clean and meaningful.
- [ ] Code adheres to SOLID principles and design patterns where appropriate.
