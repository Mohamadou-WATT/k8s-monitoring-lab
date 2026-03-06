# Kubernetes Monitoring Lab

## Overview

This project demonstrates how to deploy a complete monitoring stack in Kubernetes using Prometheus and Grafana.

The goal of this lab is to understand how to monitor Kubernetes workloads and visualize metrics using modern DevOps observability tools.

## Architecture

User → Grafana Dashboard → Prometheus → Kubernetes Cluster

Grafana visualizes metrics collected by Prometheus from the Kubernetes environment.

## Technologies Used

* Kubernetes
* Docker
* Prometheus
* Grafana
* kubectl
* YAML
* Git

## Project Structure

k8s-monitoring-lab
│
├── namespace.yaml
├── prometheus-deployment.yaml
├── prometheus-service.yaml
├── grafana-deployment.yaml
├── grafana-service.yaml
└── README.md

## Deployment Steps

### 1. Create namespace

kubectl apply -f namespace.yaml

### 2. Deploy Prometheus

kubectl apply -f prometheus-deployment.yaml
kubectl apply -f prometheus-service.yaml

### 3. Deploy Grafana

kubectl apply -f grafana-deployment.yaml
kubectl apply -f grafana-service.yaml

### 4. Verify pods

kubectl get pods -n monitoring

Expected output:

grafana-xxxxx Running
prometheus-xxxxx Running

## Access the Services

### Prometheus

kubectl port-forward svc/prometheus 9090:9090 -n monitoring

Open in browser:

http://localhost:9090

### Grafana

kubectl port-forward svc/grafana 3000:3000 -n monitoring

Open in browser:

http://localhost:3000

Default login:

admin
admin

## Configure Prometheus Data Source

In Grafana:

Connections → Data Sources → Prometheus

URL:

http://localhost:9090

Click **Save & Test**.

## Example Metrics

You can start exploring metrics such as:

up

process_cpu_seconds_total

## Learning Objectives

This lab helps understand:

* Kubernetes deployments
* Service exposure
* Observability concepts
* Monitoring architecture
* Prometheus metrics
* Grafana dashboards

## Future Improvements

Possible improvements for this project:

* Grafana alerting
* Trivy container vulnerability scanning
* CI/CD pipeline with GitHub Actions
* Kubernetes node exporter monitoring
* ELK Stack integration

## Author

Mohamadou Watt
Master 2 Networks & Cybersecurity
France
