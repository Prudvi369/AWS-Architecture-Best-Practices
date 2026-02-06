# Umbrella Helm Chart

This chart deploys 10 microservices as subcharts: `service-1` through `service-10`.

## Prerequisites
- Helm 3.x
- A Kubernetes cluster with the required permissions

## Install
```bash
helm install my-release charts/umbrella
```

## Upgrade
```bash
helm upgrade my-release charts/umbrella
```

## Uninstall
```bash
helm uninstall my-release
```

## Configuration
Global defaults apply to all services. Per-service overrides go under the service name.

Example `charts/umbrella/values.yaml`:
```yaml
global:
  image:
    repository: myrepo
    tag: "1.0.0"
    pullPolicy: IfNotPresent

service-3:
  image:
    repository: myrepo/service-3
    tag: "2.1.0"
  ingress:
    enabled: true
    hosts:
      - host: service3.example.com
        paths:
          - path: /
            pathType: Prefix
```

## Features (per service)
- Deployment and Service
- Ingress (optional)
- HPA (optional)
- ConfigMap/Secret (optional)
- ServiceAccount + RBAC (optional)
- PodDisruptionBudget (optional)
- NetworkPolicy (optional)

## Common Overrides
- `image.*` or `global.image.*`
- `replicaCount`
- `resources`
- `livenessProbe` / `readinessProbe`
- `ingress.*`
- `hpa.*`
- `config.*` / `secret.*`
- `serviceAccount.*` / `rbac.*`
- `pdb.*`
- `networkPolicy.*`
