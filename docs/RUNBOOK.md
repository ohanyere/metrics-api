# Runbook

## Service

- Name: `metrics-api`
- Team: `Payments`
- Owner: `mooref068@gmail.com`
- Cost center: `payments`

## First Checks

```bash
kubectl get rollout metrics-api -n metrics-api-dev
kubectl get pods -l app.kubernetes.io/name=metrics-api -n metrics-api-dev
kubectl logs -l app.kubernetes.io/name=metrics-api -n metrics-api-dev
```

## Health

```bash
curl https://metrics-api.dev.platform.ohanyere.internal/healthz
curl https://metrics-api.dev.platform.ohanyere.internal/readyz
curl https://metrics-api.dev.platform.ohanyere.internal/livez
```

## Rollback

```bash
kubectl argo rollouts undo metrics-api -n metrics-api-dev
```

Escalate to `Payments` through `mooref068@gmail.com` if rollback does not restore service.
