# Monitoring

This is just a complete monstrosity of a helm chart. But here's how to upgrade it...

```
helm upgrade prometheus -n monitoring prometheus-community/kube-prometheus-stack -f values.yaml -f secret-values.yaml
```
