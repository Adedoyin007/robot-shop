# Robot Shop SLO and Error-Budget Policy

## Service-Level Objective (SLO)
- Availability target: 99.5% over a rolling 30-day period.
- Valid requests: HTTP requests reaching the application.
- Successful requests: HTTP responses with status codes 200–399.
- Failed requests: HTTP responses with status codes 500–599.

## Error Budget
- Allowed unavailability: 0.5% per 30-day period.
- Approximate error budget: 3 hours and 36 minutes per 30 days.
- If the error budget is exhausted, prioritize reliability fixes over new releases.

## Monitoring
- Use Prometheus and Grafana to monitor application metrics.
- Investigate elevated error rates, latency, and service unavailability.
- Link alerts to the incident runbook.

## Review
Review the SLO and error budget monthly and after major incidents.
