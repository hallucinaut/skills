---
name: golang-expert
description: "Mastery of the Go (Golang) ecosystem, encompassing idiomatic software engineering, high-concurrency architecture, DevSecOps integration, and production-ready cloud-native deployments."
---

# Go (Golang) Expert Skill

Provide world-class expertise in Go development, covering the entire lifecycle from low-level systems programming and high-concurrency architecture to DevSecOps and large-scale distributed systems.

## When to Use

Use this skill when the user wants to:
- Architect and implement high-performance, scalable microservices or monolithic systems in Go.
- Implement complex concurrency patterns using goroutines and channels.
- Design distributed systems using gRPC, Protobuf, or message queues.
- Perform advanced performance tuning and profiling using `pprof`.
- Secure Go applications and integrate DevSecOps practices (linting, vulnerability scanning).
- Containerize Go applications for production-grade Kubernetes deployments.
- Design clean, maintainable codebases using Hexagonal or Clean Architecture.

## Core Pillars

### 1. Idiomatic Software Engineering (The "Go Way")
- **Core Language Mastery**: Deep understanding of interfaces, structs, pointers, slices, maps, and the `context` package for lifecycle management.
- **Concurrency & Parallelism**: Implementing robust patterns (Worker Pools, Fan-in/Fan-out, Pipeline, Pub/Sub) while avoiding race conditions and deadlocks.
- **Error Handling & Control Flow**: Utilizing idiomatic error wrapping (`fmt.Errorf` with `%w`), custom error types, and defensive programming.
- **Dependency Management**: Expert use of `go mod`, vendoring, and managing private modules.
- **Testing & Quality**: Comprehensive testing suites using the standard `testing` package, `testify`, mocking (using interfaces), and race detection (`go test -race`).
- **Code Quality**: Strict adherence to `gofmt`, `go vet`, and advanced linting with `golangci-lint`.

### 2. System Architecture & Distributed Systems
- **Architectural Patterns**: Implementing Clean Architecture, Hexagonal (Ports & Adapters), and Domain-Driven Design (DDD) to ensure decoupling and testability.
- **API Design**: Designing high-performance APIs using REST, gRPC (Protocol Buffers), and GraphQL.
- **Concurrency Primitives**: Expert implementation of `sync` package (Mutex, RWMutex, WaitGroup, Once, Cond) and atomic operations.
- **Distributed Communication**: Integrating with message brokers (NATS, Kafka, RabbitMQ) and implementing idempotent consumers.
- **Data Persistence**: Advanced integration with SQL (PostgreSQL, MySQL) and NoSQL (Redis, MongoDB, Cassandra) using `database/sql`, `sqlx`, or robust ORMs/query builders (Ent, GORM, SQLC).

### 3. DevSecOps & Cloud-Native Reliability
- **Observability**: Implementing structured logging (`slog`, `zerolog`), metrics (Prometheus), and distributed tracing (OpenTelemetry) for deep system visibility.
- **Security Hardening**:
    - **Vulnerability Management**: Using `govulncheck` to detect known vulnerabilities in dependencies.
    - **Secure Coding**: Preventing SQL injection, XSS, and ensuring secure handling of sensitive data.
    - **Static Analysis**: Integrating security-focused linting and scanning into CI/CD.
- **Containerization & Orchestration**: Creating highly optimized, multi-stage `Dockerfile`s (distroless/scratch images) and managing deployments on Kubernetes (K8s).
- **Continuous Integration (CI)**: Building automated pipelines that enforce linting, testing, security scans, and build-once-deploy-many principles.

### 4. Performance & Optimization
- **Profiling & Debugging**: Using `pprof` for CPU/Memory profiling, `execution traces` for goroutine scheduling analysis, and `delve` for deep debugging.
- **Memory Management**: Understanding the Go scheduler, stack vs. heap allocation, and minimizing garbage collection (GC) pressure through object pooling (`sync.Pool`) and reducing allocations.
- **Benchmarking**: Writing rigorous benchmarks (`testing.B`) to measure performance regressions and optimize hot paths.

## Deliverables

- High-performance, idiomatic, and production-ready Go source code.
- Scalable architecture designs (UML, C4 models) for distributed systems.
- Comprehensive test suites (Unit, Integration, Fuzzing, Benchmarking).
- Optimized Dockerfiles and Kubernetes manifests.
- Automated CI/CD pipeline configurations (GitHub Actions, GitLab CI).
- Detailed performance and security audit reports.

## Quality Checklist

- [ ] **Idiomatic Code**: Adheres to `effective go` and `go vet` standards.
- [ ] **Concurrency Safety**: No race conditions (verified with `-race`) and no leaked goroutines.
- [ ] **Error Handling**: Errors are checked, wrapped, and provide meaningful context.
- [ ] **Architecture**: Components are decoupled through interfaces (Ports & Adapters).
- [ ] **Security**: No hardcoded secrets; dependencies are scanned with `govulncheck`.
- [ ] **Performance**: Critical paths are benchmarked; memory allocations are minimized.
- [ ] **Observability**: Structured logs, metrics, and tracing are integrated.
- [ ] **Testing**: High coverage including edge cases and failure modes.
- [ ] **Deployment**: Uses multi-stage builds for minimal attack surface and image size.
