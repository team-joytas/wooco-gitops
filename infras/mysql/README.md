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

## MySQL Operator 버그

[mysqld-exporter v0.15.x 버전 이상](https://bugs.mysql.com/bug.php?id=112185)사용시 발생중인 버그

```
dial unix unix:///var/run/mysqld/mysql.sock: connect: no such file or directory
```

버그 수정전까지 해결 방법:

```bash
# config map 직접 수정
# https://github.com/mysql/mysql-operator/pull/39/files 참고
- socket=unix:///var/run/mysqld/mysql.sock
+ socket=/var/run/mysqld/mysql.sock
```
