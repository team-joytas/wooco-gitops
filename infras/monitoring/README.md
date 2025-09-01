# monitoring

[kube-prometheus-stack](https://github.com/prometheus-community/helm-charts/tree/main/charts/kube-prometheus-stack)

## kube prometheus stack

Release 명 상관없이 프로메테우스가 namespace 전역적으로 serviceMonitor를 바라볼 수 있지만 `monitoring/enabled: "true"` 라벨은 필수로 달아야함

example:

```yaml
apiVersion: monitoring.coreos.com/v1
kind: ServiceMonitor
metadata:
  name: example
  namespace: example
  labels:
    monitoring/enabled: "true"
spec: # ...
```

`values.yaml`의 프로메테우스 `serviceMonitor` 설정값 참고
