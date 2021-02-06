# Feast Helm Charts

## Chart: feast
=====

Feature store for machine learning. Current chart version is `0.9.2`

## Installation

https://docs.feast.dev/v/master/getting-started/deploying-feast/kubernetes

## Chart Requirements

| Repository | Name | Version |
|------------|------|---------|
|  | feast-core | 0.9.2 |
|  | feast-jobservice | 0.9.2 |
|  | feast-jupyter | 0.9.2 |
|  | feast-serving | 0.9.2 |
|  | prometheus-statsd-exporter | 0.1.2 |
| https://charts.bitnami.com/bitnami/ | kafka | 11.8.8 |
| https://charts.helm.sh/stable | grafana | 5.0.5 |
| https://charts.helm.sh/stable | postgresql | 8.6.1 |
| https://charts.helm.sh/stable | prometheus | 11.0.2 |
| https://charts.helm.sh/stable | redis | 10.5.6 |

## Chart Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| feast-core.enabled | bool | `true` | Flag to install Feast Core |
| feast-core.postgresql.existingSecret | string | `"feast-postgresql"` | Kubernetes secrets that contains the postgresql password |
| feast-jobservice.enabled | bool | `true` | Flag to install Feast Job Service |
| feast-jupyter.enabled | bool | `true` | Flag to install Feast Jupyter Notebook with SDK |
| feast-online-serving.enabled | bool | `true` | Flag to install Feast Online Serving |
| grafana.enabled | bool | `true` | Flag to install Grafana |
| kafka.enabled | bool | `true` | Flag to install Kafka |
| postgresql.enabled | bool | `true` | Flag to install Postgresql |
| postgresql.existingSecret | string | `"feast-postgresql"` | Kubernetes secrets that contains the postgresql password |
| prometheus-statsd-exporter.enabled | bool | `true` | Flag to install StatsD to Prometheus Exporter |
| prometheus.enabled | bool | `true` | Flag to install Prometheus |
| redis.enabled | bool | `true` | Flag to install Redis |
| redis.usePassword | bool | `false` | Disable redis password |