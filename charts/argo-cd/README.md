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

## Helm-secrets

Ref. <https://github.com/jkroepke/helm-secrets/wiki/ArgoCD-Integration>

### Prerequisites (Manual install once)

- Generate `age` key

```shell
age-keygen -o key.txt
```

- Create secret from key file

```shell
kubectl create secret generic helm-secrets-private-keys --from-file=key.txt -n argocd
```
