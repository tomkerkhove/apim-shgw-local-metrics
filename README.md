# Local metrics in Azure API Management's self-hosted gateway

Sandbox to setup Azure API Management's self-hosted gateway with local metrics 🤹📊

## Deployment

To install OpenTelemetry Collector:
```shell
helm install opentelemetry-collector open-telemetry/opentelemetry-collector --values deploy/opentelemetry-collector-config.yml
```

To install Azure API Management's self-hosted gateway:
```shell
helm install azure-api-management-gateway --values deploy/shgw-config.yaml azure-apim-gateway/azure-api-management-gateway
```

To install Grafana:
```shell
helm install grafana --set persistence.enabled=true grafana/grafana
```

To install StatsD Exporter:
```shell
kubectl apply -f deploy/statsd-exporter.yaml
```

To install Prometheus:
```shell
kubectl apply -f deploy/prometheus.yaml
```

To install Graphite, see [Artifact Hub](https://artifacthub.io/packages/helm/kiwigrid/graphite?modal=install).
