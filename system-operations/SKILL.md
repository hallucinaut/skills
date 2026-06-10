---
name: system-operations
description: "Automate system tasks through scripting and file operations. Manage asynchronous communication via message queues."
---

# System Operations Skill

Efficiently manage and automate system tasks and asynchronous communications.

## When to Use

Use this skill when the user wants to:
- Automate repetitive tasks via scripting (Bash, Python, etc.).
- Perform bulk file operations (renaming, moving, searching, processing).
- Implement asynchronous task processing using message queues.
- Manage system configurations.

## Core Components

### 1. Scripting & Automation
- **Bash/Shell**: For system-level automation and pipeline glue.
- **Python/Other Languages**: For complex logic, data processing, and system orchestration.
- **Task Automation**: Automating cron jobs, maintenance tasks, and system setup.

### 2. File & System Management
- **File Operations**: Efficiently handling large volumes of files (create, read, update, delete, move, bulk rename).
- **Searching & Filtering**: Using tools like `grep`, `find`, and `rg` to locate data.
- **System Monitoring**: Basic health checks of disk, CPU, and memory via scripts.

### 3. Asynchronous Messaging
- **Message Queues (MQ)**: Use brokers (e.g., RabbitMQ, Redis, Amazon SQS) to decouple services and handle background tasks.
- **Pub/Sub Pattern**: Enable one-to-many communication.
- **Worker Patterns**: Implement background workers to process tasks asynchronously from the main request/response cycle.

## Best Practices

- **Make scripts idempotent**: Running them twice shouldn't cause issues.
- **Error Handling in Scripts**: Always check exit codes and handle potential failures gracefully.
- **Logging**: Script output should be logged for auditing and debugging.
- **Security**: Be careful with permissions and sensitive data in scripts.
- **Use Task Queues for long-running tasks**: Don't block your main application thread with heavy processing.
- **Prefer standard tools**: Use tried-and-tested tools like `grep`, `sed`, `awk` when possible.

## Deliverables

- Automation scripts (Bash, Python, etc.).
- File processing utilities.
- Message queue implementation and configuration.
- Cron job / Scheduled task setup.

## Quality Checklist

- [ ] Scripts are idempotent and handle errors gracefully.
- [ ] Automation is documented and easy to run.
- [ ] File operations are safe (e.g., handling permissions and paths correctly).
- [ ] Message queues are configured for reliability (e.g., persistence, acknowledgments).
- [ ] Scripts are logged for visibility.
