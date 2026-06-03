# mini-ecommerce-gitops

GitOps manifests (Kustomize) for [Mini E-commerce DevOps Platform](https://github.com/VoAnhKiet1410/mini-ecommerce-devops).

## Layout

| Path | Purpose |
|------|---------|
| `apps/online-boutique/base/` | Happy-path services (ECR-built apps + in-cluster Redis + upstream `currencyservice`) |
| `apps/online-boutique/overlays/aws/` | ECR image tags, ALB Ingress, External Secrets |
| `clusters/aws/` | Argo CD `AppProject` + `Application` |

## AWS overlay

- **ECR account:** `962765735385` (`ap-southeast-1`)
- **Images:** `mini-ecommerce/{frontend,productcatalogservice,cartservice,checkoutservice}:latest`
- **Currency:** `us-central1-docker.pkg.dev/google-samples/microservices-demo/currencyservice:v0.10.5` (not in app CI; required for browse/cart smoke)
- **RDS secret:** `mini-ecommerce-devops/rds/master` via ESO (platform DB; apps use Redis/in-memory per Approach A)

## Validate locally

```bash
kubectl kustomize apps/online-boutique/overlays/aws | head -n 40
```

## Bootstrap on EKS

See app repo runbook: [docs/runbooks/aws-up.md](https://github.com/VoAnhKiet1410/mini-ecommerce-devops/blob/main/docs/runbooks/aws-up.md) §4–6 (ESO → Argo CD → sync → ALB smoke).
