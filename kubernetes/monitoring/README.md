# Monitoring

This is just a complete monstrosity of a helm chart. But here's how to upgrade it...

## CRDs

CRDs suffer from the following issue. https://github.com/prometheus-operator/prometheus-operator/issues/4355

Work around is to deploy CRDs sepearate to rest of stack with a create/replace style apply. So there are two apps...

- prometheus-crds
- monitoring-stack
