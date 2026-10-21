# Robot Shop Incident Postmortem

## Incident
Shipping service experienced memory pressure, causing failures and HTTP 502/500 errors.

## Impact
Some requests involving shipping and payment failed or returned server errors.

## Root Cause
The shipping service experienced Java garbage-collection pressure, reporting
"GC overhead limit exceeded". The exact underlying cause requires further investigation.

## Timeline
1. Shipping pod showed memory-related failures.
2. Application logs showed HTTP 502/500 errors.
3. Load generation was scaled down to reduce pressure.
4. Shipping deployment was restarted.
5. Shipping pod returned to a healthy running state.

## Resolution
Reduced load generation and restarted the shipping service. The service recovered.

## Lessons Learned
- Monitor memory usage and HTTP error rates.
- Configure actionable alerts and link them to the incident runbook.
- Test application capacity under load.

## Follow-up Actions
- Review shipping memory limits and application memory usage.
- Validate alert delivery.
- Run controlled load tests and document capacity limits.

## Blameless Statement
The incident exposed gaps in resource monitoring and capacity planning.
The focus is on improving system safeguards and response procedures, not blaming individuals.

## Incident Drill — Cart Pod Recovery

**Date:** 21 October 2026  
**Service:** Cart  
**Severity:** Simulated incident (controlled drill)

### What happened
The Cart pod was deliberately deleted to simulate a pod failure during an incident drill.

### Impact
Cart was briefly unavailable while Kubernetes recreated the pod.

### Detection and response
The replacement Cart pod returned to `1/1 Running`. A request to the Cart service returned an HTTP `404 Not Found` for `/`, confirming the Express service responded; `/` is not a defined Cart route.

### Root cause
No application failure was identified during this drill. The pod deletion was intentional to test Kubernetes recovery.

### Resolution
Kubernetes automatically recreated the Cart pod under its Deployment controller.

### Follow-up actions
- Verify a valid Cart API route after recovery.
- Confirm alerting and notification delivery during a future controlled incident.
