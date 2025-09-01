# valkey

[redis-sa](https://github.com/DandyDeveloper/charts/tree/master/charts/redis-ha)

redis-sa 차트에서 이미지만 valkey 8.1.x 로 변경

## FQDN

```
# haproxy
wooco-valkey-sentinel-haproxy.valkey-sentinel.svc.cluster.local

# valkey 개별 파드 (0~2 statefulset)
wooco-valkey-sentinel-announce-0.valkey-sentinel.svc.cluster.local
```

## haproxy

- `6379` 포트 RW
- `6380` 포트 RO
