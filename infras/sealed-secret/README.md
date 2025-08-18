## Sealed

```bash
kubeseal \
  --controller-name=sealed-secrets-controller \
  --controller-namespace=kube-system \
  --fetch-cert > .local/wooco-sealed-secrets-key.pub

# 또는

kubectl -n kube-system get secret sealed-secrets-key \
  -o jsonpath='{.data.tls\.crt}' | base64 -d > .local/wooco-sealed-secrets-key.pub
```
