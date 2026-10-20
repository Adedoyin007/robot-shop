# Robot Shop Incident Runbook

## Symptoms
- Increased HTTP 5xx errors
- High response latency
- Application services unavailable
- Shipping or payment failures

## Investigation
1. Check application pods:
   kubectl get pods -n robot-shop
2. Check recent events:
   kubectl get events -n robot-shop --sort-by=.lastTimestamp
3. Inspect logs for the affected service:
   kubectl logs deployment/shipping -n robot-shop --tail=100
4. Check resource usage:
   kubectl top pods -n robot-shop

## Mitigation
1. Identify the failing service and its recent errors.
2. Reduce or stop load generation if it is overwhelming the application.
3. Restart a failed deployment only when appropriate:
   kubectl rollout restart deployment/shipping -n robot-shop
4. Verify recovery:
   kubectl get pods -n robot-shop

## Escalation
Record the incident timeline, impact, mitigation, root cause, and follow-up actions.

## Recovery Criteria
Affected pods are healthy, errors return to normal, and application requests succeed.
