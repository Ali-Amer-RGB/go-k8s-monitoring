# go-k8s-monitoring
**Go Kubernetes Monitoring Lab (Minikube + Prometheus + Grafana)**

---

## Overview

This project demonstrates a simple container orchestration and monitoring workflow using Kubernetes.

A Go-based HTTP application is containerized with Docker, deployed to a local Kubernetes cluster using Minikube, and monitored using Prometheus and Grafana. The focus of this project is on understanding Kubernetes fundamentals and basic observability rather than complex application logic.

---

## What This Project Demonstrates

- Containerizing a Go application using Docker
- Deploying and managing application pods with Kubernetes
- Exposing services inside the Kubernetes cluster
- Collecting application metrics with Prometheus
- Visualizing metrics using Grafana dashboards

---

## Architecture

### Flow

1. A Go HTTP application is built and containerized using Docker
2. The Docker image is deployed to a local Kubernetes cluster (Minikube)
3. Kubernetes manages the application pods via a Deployment
4. A Kubernetes Service exposes the application internally
5. Prometheus scrapes application metrics from the `/metrics` endpoint
6. Grafana visualizes metrics such as request count and pod resource usage

---

## Tech Stack

- Go
- Docker
- Kubernetes (Minikube)
- Prometheus
- Grafana
- Helm

---

## Application Endpoints

- `/` — Returns a simple response from the Go application
- `/metrics` — Exposes Prometheus-compatible metrics

---
