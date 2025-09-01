# MySQL

[MySQL Operator](https://artifacthub.io/packages/search?repo=mysql-operator)

2.1.x 버전 : MySQL 8.4 LTS

## FQDN

```
# mysql router
wooco-mysql-cluster.mysql-cluster.svc.cluster.local

# mysql 개별 파드 (0~2 파드)
wooco-mysql-cluster-0.wooco-mysql-cluster-instances.mysql-cluster.svc.cluster.local
```

## MySQL router

- `6446` 포트 RW
- `6447` 포트 RO
- `3306` 포트 defaultPort 값 (기본값 mysql-rw)

## sealed

```bash
CURR_PROJ_DIR=$(git rev-parse --show-toplevel)

kubeseal --format=yaml \
  --cert=$CURR_PROJ_DIR/.local/wooco-sealed-secrets-key.pub \
  < $CURR_PROJ_DIR/infras/mysql/secrets.yaml\
  > $CURR_PROJ_DIR/infras/mysql/sealed-secrets.yaml
```
