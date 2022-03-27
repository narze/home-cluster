# Self-managed ArgoCD Chart

Ref: <https://www.arthurkoziel.com/setting-up-argocd-with-helm>

## Update chart

```shell
helm repo add argo-cd https://argoproj.github.io/argo-helm
helm dep update charts/argo-cd/
```

## Bootstrap ArgoCD

```shell
helm install argo-cd charts/argo-cd/ -n argocd --create-namespace # First Time
helm upgrade argo-cd charts/argo-cd/ -n argocd # Update values

helm show values charts/argo-cd/ # Check values
```
