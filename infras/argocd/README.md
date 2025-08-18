## Bootstrap

```bash
kubectl kustomize --enable-helm ./infras/argocd | kubectl apply -f -
```

## 초기 admin 비밀번호 확인

```bash
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```
