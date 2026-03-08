# homelab-k8s-base-gitops
For deploying to homelab k8s cluster using FluxCD

## Prerequisites

### GitHub Status Reporting
To enable Flux to report deployment status back to GitHub commits, you must create a Kubernetes Secret with a GitHub Personal Access Token (PAT).

1. **Create a GitHub PAT** with `repo:status` (Classic) or **Commit statuses** (Fine-grained) permissions.
2. **Apply the secret** to your cluster:

```bash
kubectl create secret generic github-token \
  --namespace=flux-system \
  --from-literal=token=YOUR_GITHUB_TOKEN
```

*Note: The `infrastructure/notifications/github-status.yaml` manifest expects a secret named `github-token` in the `flux-system` namespace.*
