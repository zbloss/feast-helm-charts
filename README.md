# Feast Helm Charts

This repo contains all Feast Helm charts and their configuration parameters.

This repository contains multiple Helm charts. 
* Feast: The complete Helm chart containing all Feast components and dependencies. Most users will use this chart.
    * Feast Core: The Feast Core (Registry) Helm chart only.
    * Feast Serving: The Feast Serving Helm chart only. For teams that only want to install Feast Serving to serve features online.
    * Feast Jupyter: The Feast Jupyter Helm chart. This helm chart installs a Jupyter notebook into a cluster which has Feast dependencies pre-installed.
    * Feast Job Service: The Feast Job Service Helm chart. This chart installs the Feast Job Service which allows for the automatic management and execution of jobs.
    * Redis: (Dependency) Used as an online store by Feast Serving
    * Postgres: (Dependency) Used as a backend to Feast Core. Feature definitions are stored in Postgres.
    * Optional Dependencies: The wrapping Feast chart also contains Grafana, Prometheus, Statsd-exporter, and Kafka as dependencies. These sub charts are for convenience only. They are not required for Feast to function.

## Chart: Feast

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