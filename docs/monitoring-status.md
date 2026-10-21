# Robot Shop Monitoring Status

## Verified
- Robot Shop application deployed on EKS.
- kube-prometheus-stack installed.
- Prometheus loaded the RobotShopPodNotReady alert rule.
- Temporary test alert successfully fired in Prometheus and was deleted after verification.
- Alert rule links to docs/incident-runbook.md.
- Fluent Bit, Loki, and Jaeger pods are running.
- Grafana successfully connected to Loki using the X-Scope-OrgID header.
- Log search verified in Grafana Explore.
- Jaeger UI and trace search verified.
- Jaeger OTLP HTTP ingestion verified.
- OpenTelemetry auto-instrumentation configured for the Cart Node.js service.
- Real Cart traces verified in Jaeger on 21 October 2026.
- Observed GET /, GET /metrics, and Redis-related spans.
- Eleven Cart traces observed during verification.
- Cart memory request increased to 128Mi and limit to 256Mi after OOM kills.

## Pending
- Slack notification delivery requires a Slack workspace and incoming webhook.
- Complete incident drill and document the observed root cause and mitigation.
- Export and verify the final Grafana dashboard.

## Supporting Documentation
- docs/slo-error-budget.md
- docs/incident-runbook.md
- docs/incident-postmortem.md
- monitoring/grafana/robot-shop-application-metrics.json
- monitoring/alerts/robot-shop-alerts.yaml
- monitoring/logging/fluent-bit-values.yaml
