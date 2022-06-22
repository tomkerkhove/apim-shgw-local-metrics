# Local metrics in Azure API Management's self-hosted gateway

Sandbox to setup Azure API Management's self-hosted gateway with local metrics 🤹📊

## Deployment

To install OpenTelemetry Collector:
```shell
helm install opentelemetry-collector open-telemetry/opentelemetry-collector --values deploy/opentelemetry-collector-config.yml
```

To install Azure API Management's self-hosted gateway:
```shell
helm install azure-api-management-gateway --set gateway.configuration.uri='<apim-tenant>.configuration.azure-api.net' --set gateway.auth.key='<auth token>' --set observability.opentelemetry.enabled=true --set observability.opentelemetry.collector.uri=http://opentelemetry-collector:4317 --set service.type=LoadBalancer azure-apim-gateway/azure-api-management-gateway
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
