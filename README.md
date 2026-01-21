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

**Screenshots of my efforts and results including some descriptions:**


**Firstly I ensured that I have installed Ubuntu, enabled WSL integration and installed Minikube onto the system. And then I cloned this repo, created the project files onto WSL and then pushed them to the repo:**
<img width="826" height="338" alt="Screenshot 2026-01-21 132608" src="https://github.com/user-attachments/assets/191bafea-0f32-4c83-947c-736f6ec66e2b" />
<br>
<br>
<img width="632" height="258" alt="Screenshot 2026-01-21 133905" src="https://github.com/user-attachments/assets/2247d824-a1d2-4b21-93b2-6873cb06d863" />
<br>
<br>
<img width="1089" height="393" alt="Screenshot 2026-01-21 134048" src="https://github.com/user-attachments/assets/7305f997-fa14-4ac7-b3e2-c922cd238dde" />
<br>
<br>
<br>
<br>
<br>
<br>

**I ran into a big mess trying to initialise Minikube through Docker driver on WSL so I decided to do this via Powershell, the error was mostly due to Minikune on Windows' connectivity issues with the API server. Here, Minikube Kubernetes cluster was successfully started using the Docker driver and verified with kubectl.:**
<img width="1298" height="638" alt="Screenshot 2026-01-21 160316" src="https://github.com/user-attachments/assets/74fac8fd-d415-4283-b16f-ef869e324eb6" />
<br>
<br>
<br>
<br>
<br>
<br>

**I built a Docker image for my Go app and deployed it to a local Kubernetes cluster using Minikube. Then I checked that the pods were running and exposed the service so I could access the app in the browser.**


<img width="2163" height="1242" alt="Screenshot 2026-01-21 160632" src="https://github.com/user-attachments/assets/500d41cd-d3d2-4109-a4aa-d609d1023208" />
<img width="1006" height="277" alt="Screenshot 2026-01-21 160849" src="https://github.com/user-attachments/assets/fe8c86d7-3885-45e1-b47b-76e5c4c74c23" />
<img width="1340" height="608" alt="Screenshot 2026-01-21 161029" src="https://github.com/user-attachments/assets/206cceec-59eb-4efe-83e5-0d97153531ac" />
<img width="486" height="181" alt="Screenshot 2026-01-21 161050" src="https://github.com/user-attachments/assets/583be68e-fcc7-47bd-8919-2da679fc67d3" />









