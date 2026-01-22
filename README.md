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

**I built a Docker image for my Go app and deployed it to a local Kubernetes cluster using Minikube. Then I checked that the pods were running and exposed the service so I could access the app in the browser:**


<img width="2163" height="1242" alt="Screenshot 2026-01-21 160632" src="https://github.com/user-attachments/assets/500d41cd-d3d2-4109-a4aa-d609d1023208" />
<br>
<br>
<img width="1006" height="277" alt="Screenshot 2026-01-21 160849" src="https://github.com/user-attachments/assets/fe8c86d7-3885-45e1-b47b-76e5c4c74c23" />
<br>
<br>
<img width="1340" height="608" alt="Screenshot 2026-01-21 161029" src="https://github.com/user-attachments/assets/206cceec-59eb-4efe-83e5-0d97153531ac" />
<br>
<br>
<img width="486" height="181" alt="Screenshot 2026-01-21 161050" src="https://github.com/user-attachments/assets/583be68e-fcc7-47bd-8919-2da679fc67d3" />
<br>
<br>
<br>
<br>
<br>
<br>

**This page shows that the Go app is exposing metrics at the /metrics endpoint. It confirms that Prometheus can collect performance data from the application for monitoring in Grafana:**

<img width="1185" height="1336" alt="Screenshot 2026-01-21 161117" src="https://github.com/user-attachments/assets/6ac75eed-2f90-4565-a878-a17693c7d8de" />
<br>
<br>
<br>
<br>
<br>
<br>


**I installed Helm on Windows using winget, added the Prometheus community Helm repository, and updated it. Then I used Helm to deploy the kube-prometheus-stack, which installed Prometheus, Grafana, and related monitoring components into my Kubernetes cluster successfully:**

<img width="1392" height="459" alt="Screenshot 2026-01-21 162133" src="https://github.com/user-attachments/assets/509931df-236f-4fe2-bc26-f9d139fad433" />
<br>
<br>
<img width="2099" height="1189" alt="Screenshot 2026-01-21 162357" src="https://github.com/user-attachments/assets/779594d7-0f5b-4464-a340-e241aebd86ee" />
<br>
<br>
<br>
<br>
<br>
<br>

**I installed the Prometheus and Grafana monitoring stack using Helm in a dedicated monitoring namespace and verified that all monitoring pods were running successfully. I then retrieved the Grafana admin password, port-forwarded the Grafana service, and accessed the Grafana dashboard locally to confirm the setup was working:**

<img width="1106" height="999" alt="Screenshot 2026-01-21 163528" src="https://github.com/user-attachments/assets/5318bd25-07da-4b3f-bebe-bdfa98a4c275" />
<br>
<br>
<img width="1092" height="275" alt="Screenshot 2026-01-21 163605" src="https://github.com/user-attachments/assets/9678fc56-8dd9-49ac-8b49-bc7d12184cba" />
<br>
<br>
<img width="1087" height="388" alt="Screenshot 2026-01-21 163817" src="https://github.com/user-attachments/assets/e411ca40-0bce-4d40-acce-6603bcb48b90" />
<br>
<br>
<br>
<br>
<br>
<br>


**I logged into Grafana using the admin account and accessed it through a local port-forward on localhost:3000. After logging in, I confirmed that Grafana was successfully connected to Prometheus by running queries and seeing live Kubernetes metrics displayed in the Explore dashboard:**

<img width="952" height="929" alt="Screenshot 2026-01-21 163856" src="https://github.com/user-attachments/assets/2ae9ce87-fc23-4416-a141-6bf49475a689" />
<br>
<br>
<img width="2531" height="1331" alt="Screenshot 2026-01-21 164318" src="https://github.com/user-attachments/assets/1dca109c-2dfd-491e-ad00-c17d8b8ebd52" />
<br>
<br>
<br>
<br>
<br>
<br>

**I created a ServiceMonitor YAML file to tell Prometheus how to scrape metrics from my go-demo service on the /metrics endpoint. Then I applied it to the cluster, which successfully registered the service so Prometheus could collect the application metrics:**

<img width="731" height="419" alt="Screenshot 2026-01-21 175854" src="https://github.com/user-attachments/assets/b30f9a76-7d9e-4e80-94cd-57237a149a5e" />
<br>
<br>
<img width="1096" height="351" alt="Screenshot 2026-01-21 180249" src="https://github.com/user-attachments/assets/0dfd5b01-3a3d-4c50-a7ee-752adcb72955" />
<br>
<br>
<br>
<br>
<br>
<br>

**I listed all ServiceMonitors in the monitoring namespace to confirm that my custom go-demo ServiceMonitor was created successfully. This shows Prometheus is now aware of my application and can scrape its metrics along with the default Kubernetes components:**
<img width="1079" height="354" alt="Screenshot 2026-01-21 180316" src="https://github.com/user-attachments/assets/1a04b9cc-a751-4c8c-b1ce-909b0366be32" />
<br>
<br>
<br>
<br>
<br>
<br>

**I port-forwarded Prometheus and Grafana services so I could access them in the browser, and confirmed Prometheus was running by opening its /ready and metrics endpoints. Then I opened Grafana, queried the http_requests_total metric, and verified that my Go app metrics were successfully being collected and visualised:**

<img width="2521" height="1362" alt="Screenshot 2026-01-21 180942" src="https://github.com/user-attachments/assets/06855204-4e3c-45b1-b7a7-c396cd509497" />
<br>
<br>
<img width="2261" height="1106" alt="Screenshot 2026-01-21 181652" src="https://github.com/user-attachments/assets/cdf9b4fd-0c5d-413a-905e-2bab5e3f1cc7" />







