# Feast Helm Charts

This repo contains all Feast Helm charts and their configuration options.

This repository contains multiple Helm charts.
* Feast (root chart): The complete Helm chart containing all Feast components and dependencies. Most users will use this chart, but can selectively enable/disable subcharts using the values.yaml file.
    * [Feast Core](charts/feast-core): The Feast Core (Registry) Helm chart only.
    * [Feast Serving](charts/feast-serving): The Feast Serving Helm chart only. For teams that only want to install Feast Serving to serve features online.
    * [Feast Job Service](charts/feast-jobservice): The Feast Job Service Helm chart. This chart installs the Feast Job Service which allows for the automatic management and execution of jobs.
    * [Feast Jupyter](charts/feast-jupyter) (Optional): The Feast Jupyter Helm chart. This chart is not required to use Feast. The Helm chart installs a Jupyter notebook into a cluster which has Feast dependencies pre-installed.
    * Redis: (Dependency) Used as an online store by Feast Serving
    * Postgres: (Dependency) Used as a backend to Feast Core. Feature definitions are stored in Postgres.
    * Kafka (Optional): Kafka Helm chart. Not a dependency. Only added for convenience and for use in tutorials
    * Prometheus (Optional): Prometheus Helm chart. Not a dependency. Only provided for convenient.
    * Statsd Exporter (Optional): Statsd Exporter Helm chart. Used as exporter in order to publish metrics for Prometheus.
    * Grafana (Optional): Grafana Helm chart. Not a dependency. Only provided for convenience in order to visualize Prometheus metrics.

## Chart: Feast

Feature store for machine learning Current chart version is `0.100.3`

## Installation

Charts are published to `https://feast-helm-charts.storage.googleapis.com`. Please note that this URL is different from the URL we previously used (`feast-charts`)

Run the following commands to add the repository

```
helm repo add feast-charts https://feast-helm-charts.storage.googleapis.com
helm repo update
```

Make sure to create a Postgres secret prior to installation
```
kubectl create secret generic feast-postgresql --from-literal=postgresql-password=password
```

Install Feast
```
helm install feast-release feast-charts/feast
```

For more details, please see: https://docs.feast.dev/v/master/getting-started/deploying-feast/kubernetes

## Chart Requirements

| Repository | Name | Version |
|------------|------|---------|
|  | feast-jobservice | 0.9.2 |
|  | feast-jupyter | 0.9.2 |
| https://charts.bitnami.com/bitnami/ | kafka | 11.8.8 |
| https://charts.helm.sh/stable | postgresql | 8.6.1 |
| https://charts.helm.sh/stable | redis | 10.5.6 |
| https://feast-helm-charts.storage.googleapis.com | feast-core | 0.25.0 |
| https://feast-helm-charts.storage.googleapis.com | feast-serving | 0.25.0 |

## Chart Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| feast-core.enabled | bool | `true` | Flag to install Feast Core |
| feast-core.image.repository | string | `"gcr.io/kf-feast/feast-core"` |  |
| feast-core.image.tag | string | `"develop"` |  |
| feast-core.postgresql.existingSecret | string | `"feast-postgresql"` | Kubernetes secrets that contains the postgresql password |
| feast-jobservice.enabled | bool | `true` | Flag to install Feast Job Service |
| feast-jobservice.image.repository | string | `"gcr.io/kf-feast/feast-jobservice"` |  |
| feast-jobservice.image.tag | string | `"develop"` |  |
| feast-jupyter.enabled | bool | `true` | Flag to install Feast Jupyter Notebook with SDK |
| feast-jupyter.image.repository | string | `"gcr.io/kf-feast/feast-jupyter"` |  |
| feast-jupyter.image.tag | string | `"develop"` |  |
| feast-serving.enabled | bool | `true` |  |
| feast-serving.image.repository | string | `"gcr.io/kf-feast/feast-serving"` |  |
| feast-serving.image.tag | string | `"develop"` |  |
| kafka.enabled | bool | `true` | Flag to install Kafka |
| postgresql.enabled | bool | `true` | Flag to install Postgresql |
| postgresql.existingSecret | string | `"feast-postgresql"` | Kubernetes secrets that contains the postgresql password |
| redis.enabled | bool | `true` | Flag to install Redis |
| redis.usePassword | bool | `false` | Disable redis password |