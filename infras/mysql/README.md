## sealed

```bash
CURR_PROJ_DIR=$(git rev-parse --show-toplevel)

kubeseal --format=yaml \
  --cert=$CURR_PROJ_DIR/.local/wooco-sealed-secrets-key.pub \
  < $CURR_PROJ_DIR/infras/mysql/root-password.yaml \
  > $CURR_PROJ_DIR/infras/mysql/sealed-root-password.yaml
```
