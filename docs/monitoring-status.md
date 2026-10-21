# Robot Shop Monitoring Status

## Verified
- Robot Shop pods were checked and were Running and Ready.
- kube-prometheus-stack is installed.
- Prometheus loaded the RobotShopPodNotReady alert rule.
- The alert is currently Inactive because its condition is not triggering.
- The alert includes a link to docs/incident-runbook.md.
- Fluent Bit, Loki, and Jaeger pods are running.
- Grafana successfully connected to Loki using the X-Scope-OrgID header.
- Loki log search was verified in Grafana Explore.
- Jaeger UI, trace search, and span details were verified.
- Jaeger OTLP HTTP ingestion was verified with synthetic test traces.
- Robot Shop application-level tracing remains pending instrumentation.

## Pending Verification
- Slack notification delivery: requires a Slack workspace and incoming webhook.
- Robot Shop application tracing: requires OpenTelemetry instrumentation.
- Alert firing: verified with a temporary Prometheus test alert, which was then deleted.

## Next Actions
- Instrument a Robot Shop service with OpenTelemetry and confirm an application trace in Jaeger.
- Configure notification delivery if a Slack workspace becomes available.

### OpenTelemetry tracing verification

- Instrumented the Cart Node.js service with OpenTelemetry auto-instrumentation.
- Configured OTLP HTTP export to Jaeger at `http://jaeger.monitoring.svc.cluster.local:4318`.
- Increased Cart memory limits to 256Mi and requests to 128Mi to prevent OOM kills.
- Verified real Cart traces in Jaeger on 21 October 2026.
- Observed HTTP traces for `GET /` and `GET /metrics`, along with Redis-related spans.
- Jaeger displayed 11 traces during verification.
