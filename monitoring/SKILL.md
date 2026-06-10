---
name: monitoring
description: "Set up monitoring, logging, and observability for applications. Use when implementing dashboards, alerting, metrics collection, or troubleshooting."
---

# Monitoring Skill

Implement monitoring, logging, and observability for applications.

## When to Use

Use this skill when the user wants to:
- Set up metrics collection
- Create monitoring dashboards
- Configure alerting rules
- Implement structured logging
- Set up distributed tracing
- Work with observability tools
- Performance monitoring

## Observability Pillars

### 1. Metrics (The "What")
Quantitative data about your system over time.
- **Counter**: Monotonically increasing values (e.g., total requests, error counts).
- **Gauge**: Values that can go up and down (e.g., current memory usage, active users).
- **Histogram**: Distribution of values (e.g., request latency).
- **Summary**: Similar to histogram, but provides quantiles (e.g., p95, p99 latency).

### 2. Logging (The "Why")
Qualitative data providing context for events.
- **Structured Logs**: Using JSON format to make logs easily searchable and machine-readable.
- **Log Levels**: Using appropriate levels (DEBUG, INFO, WARN, ERROR, FATAL) to control verbosity.
- **Correlation IDs**: Injecting unique IDs into every request to trace it through multiple microservices.

### 3. Tracing (The "Where")
Visualizing the path of a single request across distributed systems.
- **Distributed Tracing**: Using spans and traces to identify latency bottlenecks in complex architectures.
- **Context Propagation**: Passing trace IDs through service boundaries.

## Monitoring Stack Options

### Metrics & Visualization
- **Prometheus**: Pull-based metrics collection and time-series database.
- **Grafana**: Powerful visualization and dashboarding tool for Prometheus, SQL, etc.
- **CAdvisor/Node Exporter**: For container and host-level metrics.

### Logging Aggregation
- **ELK Stack**: Elasticsearch, Logstash, Kibana.
- **EFK Stack**: Elasticsearch, Fluentd, Kibana.
- **Loki**: Log aggregation system inspired by Prometheus.

### Distributed Tracing
- **OpenTelemetry**: The industry standard for generating and collecting observability data.
- **Jaeger / Zipkin**: Tools for visualizing and analyzing traces.

## Implementation Examples

### Python: Structured Logging with JSON
```python
import logging
import json
import time

class JsonFormatter(logging.Formatter):
    def format(self, record):
        log_record = {
            "timestamp": self.formatTime(record, self.datefmt),
            "level": record.levelname,
            "message": record.getMessage(),
            "module": record.module,
            "correlation_id": getattr(record, 'correlation_id', 'N/A')
        }
        return json.dumps(log_record)

logger = logging.getLogger("app")
handler = logging.StreamHandler()
handler.setFormatter(JsonFormatter())
logger.addHandler(handler)
logger.setLevel(logging.INFO)

# Usage with context
correlation_id = "req-12345"
logger.info("User logged in", extra={"correlation_id": correlation_id})
```

### Prometheus: Custom Metrics (Python/Prometheus Client)
```python
from prometheus_client import Counter, Histogram, start_http_server
import time
import random

# Define metrics
REQUEST_COUNT = Counter('http_requests_total', 'Total HTTP Requests', ['method', 'endpoint'])
REQUEST_LATENCY = Histogram('http_request_duration_seconds', 'HTTP request latency')

if __name__ == '__main__':
    # Start Prometheus metrics server on port 8000
    start_http_server(8000)
    print("Server started on port 8000")
    
    while True:
        with REQUEST_LATENCY.time():
            # Simulate an HTTP request
            method = random.choice(['GET', 'POST'])
            endpoint = random.choice(['/api/data', '/api/user'])
            
            # Simulate processing time
            time.sleep(random.uniform(0.1, 0.5))
            
            REQUEST_COUNT.labels(method=method, endpoint=endpoint).inc()
```

## Best Practices

- **Log everything important**: Errors, warnings, and critical user actions.
- **Use meaningful log levels**: Don't spam with DEBUG in production.
- **Structure your logs**: Use JSON for easy parsing by aggregation tools.
- **Add context**: Always include request IDs, user IDs, and timestamps.
- **Monitor what matters**: Focus on the "Four Golden Signals": Latency, Traffic, Errors, and Saturation.

## Common Pitfalls

- **Alert Fatigue**: Setting too many low-priority alerts that get ignored by engineers.
- **Logging Sensitive Data**: Accidentally logging passwords, tokens, or PII.
- **High Cardinality Metrics**: Using high-cardinality labels (like User ID) in Prometheus metrics, which can crash the monitoring system.
- **Lack of Dashboards**: Collecting data but never visualizing it to spot trends and anomalies.

## Deliverables

- Monitoring configuration files (Prometheus rules, Grafana dashboards).
- Alerting rules and notification configurations.
- Log aggregation setup and retention policies.
- Distributed tracing implementation.
- Documentation for monitoring and troubleshooting.

## Quality Checklist

- [ ] Critical business metrics are monitored.
- [ ] Alerts are actionable and have clear severity levels.
- [ ] Logs are structured (JSON) and searchable.
- [ ] Metrics use appropriate types (Counter, Gauge, etc.).
- [ ] Distributed tracing is implemented for complex flows.
- [ ] Dashboards provide a clear view of system health.
