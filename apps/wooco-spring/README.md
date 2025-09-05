## wooco-spring

### sealed

```bash
CURR_PROJ_DIR=$(git rev-parse --show-toplevel)

kubeseal --format=yaml \
  --cert=$CURR_PROJ_DIR/.local/wooco-sealed-secrets-key.pub \
  < $CURR_PROJ_DIR/apps/wooco-spring/base/registry-cred.yaml \
  > $CURR_PROJ_DIR/apps/wooco-spring/base/sealed-registry-cred.yaml
```

```bash
CURR_PROJ_DIR=$(git rev-parse --show-toplevel)

kubeseal --format=yaml \
  --cert=$CURR_PROJ_DIR/.local/wooco-sealed-secrets-key.pub \
  < $CURR_PROJ_DIR/apps/wooco-spring/overlay/prod/secrets.yaml \
  > $CURR_PROJ_DIR/apps/wooco-spring/overlay/prod/sealed-secrets.yaml
```
