## Sealed

```bash
CURR_PROJ_DIR=$(git rev-parse --show-toplevel)

kubeseal --format=yaml \
  --cert=$CURR_PROJ_DIR/.local/wooco-sealed-secrets-key.pub \
  < $CURR_PROJ_DIR/infras/cert-manager/cloudflare-secret.yaml \
  > $CURR_PROJ_DIR/infras/cert-manager/sealed-cloudflare-secret.yaml
```
