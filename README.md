# mini-ecommerce-gitops

GitOps manifests (Kustomize) for [Mini E-commerce DevOps Platform](https://github.com/VoAnhKiet1410/mini-ecommerce-devops).

## Layout (Phase 3)

- `apps/online-boutique/base/` — Kustomize base (happy-path services)
- `apps/online-boutique/overlays/aws/` — ECR images, ingress, ESO
- `clusters/aws/` — Argo CD Application and AppProject
- `observability/aws/` — Prometheus / Grafana

Phase 0: repository placeholder. Manifests added in Phase 3.
