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
- Manage system configurations and deployments.

## Core Components

### 1. Scripting & Automation
- **Bash/Shell**: For lightweight system-level automation, glue code for pipelines, and managing OS-level tasks.
- **Python/Other Languages**: For complex logic, data processing, API orchestration, and cross-platform automation.
- **Task Automation**: Automating cron jobs, maintenance tasks (log rotation, cleanup), and system setup/provisioning.

### 2. File & System Management
- **File Operations**: Efficiently handling large volumes of files (create, read, update, delete, bulk rename, find/replace).
- **Searching & Filtering**: Using powerful tools like `grep`, `find`, `sed`, `awk`, and `ripgrep` (`rg`) to locate and manipulate data.
- **System Monitoring**: Implementing basic health checks (disk space, CPU usage, memory consumption) via scripts or monitoring agents.

### 3. Asynchronous Messaging
- **Message Queues (MQ)**: Use brokers (e.g., RabbitMQ, Redis, Amazon SQS, Kafka) to decouple services and handle background tasks reliably.
- **Pub/Sub Pattern**: Enable one-to-many communication where multiple subscribers react to a single event.
- **Worker Patterns**: Implement background workers to process heavy or slow tasks (e.g., image processing, email sending) asynchronously from the main request/response cycle.

## Implementation Examples

### Bash: Automated Log Cleanup
```bash
#!/bin/bash
# Cleanup logs older than 7 days in /var/log/myapp/
LOG_DIR="/var/log/myapp"
RETENTION_DAYS=7

if [ -d "$LOG_DIR" ]; then
    find "$LOG_DIR" -name "*.log" -type f -mtime +$RETENTION_DAYS -exec rm -f {} \;
    echo "$(date): Cleanup completed in $LOG_DIR" >> /var/log/myapp_cleanup.log
else
    echo "$(date): Error: Directory $LOG_DIR not found." >&2
fi
```

### Python: Batch File Renaming
```python
import os

def batch_rename(directory, prefix):
    for filename in os.listdir(directory):
        if filename.endswith(".txt"):
            new_name = f"{prefix}_{filename}"
            os.rename(os.path.join(directory, filename), os.path.join(directory, new_name))
            print(f"Renamed: {filename} -> {new_name}")

batch_rename("./logs", "processed")
```

### Python: Simple Redis-based Task Queue (Conceptual)
```python
import redis
import time

r = redis.Redis(host='localhost', port=6379, db=0)

def worker():
    print("Worker started. Waiting for tasks...")
    while True:
        # BLPOP is a blocking pop; it waits until an item is available
        task = r.blpop('task_queue', timeout=0)
        if task:
            task_data = task[1].decode('utf-8')
            print(f"Processing task: {task_data}")
            time.sleep(2) # Simulate work
            print(f"Task {task_data} completed.")

if __name__ == "__main__":
    worker()
```

## Best Practices

- **Make scripts idempotent**: Ensure that running the script multiple times results in the same state without errors or duplicate side effects.
- **Error Handling & Exit Codes**: Always check exit codes and handle potential failures gracefully. Use `set -e` in Bash for immediate exit on error.
- **Logging & Auditing**: Script output should be logged to a file or centralized logging system for auditing and debugging.
- **Security (Least Privilege)**: Run scripts with the minimum necessary permissions. Avoid hardcoding secrets; use environment variables or secret managers.
- **Use Task Queues for Long-Running Tasks**: Never block your main application thread with heavy processing; offload it to background workers.
- **Prefer Standard Tools**: Use tried-and-tested tools like `grep`, `sed`, `awk`, and `find` for efficiency and reliability.

## Common Pitfalls

- **Lack of Idempotency**: Scripts that fail halfway through and leave the system in an inconsistent state when re-run.
- **Hardcoding Paths/Secrets**: Makes scripts non-portable and insecure.
- **Ignoring Errors**: Not checking if a command succeeded before proceeding to the next step.
- **Over-reliance on Shell Scripts for Complex Logic**: When logic gets complex, switch to a robust language like Python.

## Deliverables

- Automation scripts (Bash, Python, etc.).
- File processing and cleanup utilities.
- Message queue implementation and worker configurations.
- Cron job / Scheduled task setups.

## Quality Checklist

- [ ] Scripts are idempotent and handle errors gracefully.
- [ ] Automation is documented and easy to run.
- [ ] File operations are safe (e.g., handling permissions and paths correctly).
- [ ] Message queues are configured for reliability (e.g., persistence, acknowledgments).
- [ ] Scripts are logged for visibility and auditing.
