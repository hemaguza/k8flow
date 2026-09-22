# ⚡ K8Flow

<div align="center">

### **K8Flow by Neihec**
#### *The Intelligent, Visual Kubernetes Management Platform & DevOps Console with FlowBot AI*

**Created & Maintained by [@hemaguza](https://github.com/hemaguza) • Powered by [Neihec](mailto:soporte@neihec.com)**

<br/>

[![Kubernetes](https://img.shields.io/badge/kubernetes-%23326ce5.svg?style=for-the-badge&logo=kubernetes&logoColor=white)](https://kubernetes.io/)
[![Go](https://img.shields.io/badge/Go-00ADD8?style=for-the-badge&logo=go&logoColor=white)](https://golang.org/)
[![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)](https://reactjs.org/)
[![TailwindCSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)](https://tailwindcss.com/)
[![Enterprise-Neihec](https://img.shields.io/badge/Enterprise-Neihec-blue.svg?style=for-the-badge)](mailto:soporte@neihec.com)
[![License](https://img.shields.io/badge/License-Community%20%2F%20Business-indigo.svg?style=for-the-badge)](https://github.com/hemaguza/k8flow)

</div>

---

## 🌟 What is K8Flow?

**K8Flow** is an enterprise-grade Kubernetes control panel and cloud-native application orchestrator developed by **hemaguza** for **Neihec**. It simplifies Kubernetes management by combining intuitive visual control for workloads, networking, and persistent storage with **FlowBot AI**, an integrated cluster copilot powered by modern LLMs (OpenAI, Gemini, Ollama, DeepSeek) for real-time telemetry diagnostics and automated manifest generation.

---

## 🚀 1-Minute Quickstart

Deploy K8Flow directly to any Kubernetes cluster (KinD, k3s, Minikube, EKS, GKE, AKS, Bare Metal):

```bash
kubectl apply -f https://raw.githubusercontent.com/hemaguza/k8flow/main/install.yaml
```

Wait for the deployment rollout to complete:

```bash
kubectl rollout status deployment/k8flow-console -n k8flow-system
```

### 🌐 Access the Web Console

Open your browser and navigate to:
```text
http://<YOUR_NODE_IP>:30080
```

> **Default Initial Credentials:**
> - **Username:** `admin`
> - **Password:** `admin`
>
> *(Make sure to update your credentials in the Profile / Security modal upon first login).*

---

## ✨ Key Features

| Feature | Description |
| :--- | :--- |
| 🤖 **FlowBot AI Copilot** | Automated cluster diagnostics, real-time crash loop log analysis, remediation recommendations, and zero-touch YAML patch generation. |
| 📦 **Visual Workload Management** | Create, edit, scale, and restart Deployments, StatefulSets, DaemonSets, and Jobs with intuitive interactive forms. |
| 🔒 **Automatic SSL / TLS Certificates** | Full ACME / Let's Encrypt integration via cert-manager. Auto-renew certificates and attach SSL to Ingresses with 1 click. |
| 💾 **Storage & PVC Management** | Provision Persistent Volume Claims, browse storage classes, and monitor capacity and access modes (RWO / RWX). |
| 📈 **Resource Quotas & Multi-Project RBAC** | Isolate projects with granular CPU, memory, and pod limits. Role-based access control (`Cluster Admin`, `Project Admin`, `Developer`, `Viewer`). |
| 🐳 **Private OCI Registry Explorer** | Connect to Harbor, Docker Hub, GHCR, AWS ECR, and local registries. Browse catalog tags, architectures, and sync `imagePullSecrets` across namespaces. |
| 💻 **Web Terminal & Live Logs** | Interactive container terminal (WebSocket-based `kubectl exec`) and multi-stream live log viewer with search and pre-crash historical retention. |
| 🌍 **Multi-Language Support** | Full internationalization out of the box in **English (`en`)**, **Spanish (`es`)**, and **Portuguese (`pt`)**. |

---

## 🏗️ Architecture Overview

```
                          ┌────────────────────────┐
                          │  K8Flow Web Console    │ (React 18 + Tailwind)
                          │   (NodePort: 30080)    │
                          └───────────┬────────────┘
                                      │ REST / WebSocket
                                      ▼
                          ┌────────────────────────┐
                          │     K8Flow API Hub     │ (Golang REST Engine)
                          │   (ClusterIP: 8080)    │
                          └───────────┬────────────┘
                                      │ Kubernetes API / CRDs
                                      ▼
       ┌─────────────────────────────────────────────────────────────┐
       │                 Kubernetes Cluster Runtime                  │
       │  ┌─────────────────────────┐   ┌─────────────────────────┐  │
       │  │    K8Flow Operator      │   │    Cluster Resources    │  │
       │  │ (Custom CRD Controller) │   │ (Pods, PVCs, Ingresses) │  │
       │  └─────────────────────────┘   └─────────────────────────┘  │
       └─────────────────────────────────────────────────────────────┘
```

---

## 📋 Requirements

- **Kubernetes**: `v1.24+`
- **Node Resources**: Minimum `2 CPU Cores`, `4 GB RAM`
- **Storage**: Any standard `StorageClass` (Local Path, Longhorn, Ceph, EBS, etc.)
- **Ingress Controller** *(Optional for external routing)*: `ingress-nginx` or `traefik`

---

## 💎 Editions & Licensing

K8Flow is distributed by **Neihec** under a dual-tier model:

- **Community Edition (Free)**: Core visual management, FlowBot AI diagnostics, visual editors, storage/network management, limited up to **5 Namespaces / Projects**, **10 RBAC Users**, and **50 Workload Pods**.
- **Business Edition**: **Unlimited namespaces, unlimited users, and unlimited pods**, enterprise RBAC audit trails, priority FlowBot AI integrations, dedicated support, and custom branding.

### 📩 Commercial Inquiries & License Activation
To purchase a Business license, request an enterprise trial, or obtain technical support:
- 📧 **Support & Sales Email:** [soporte@neihec.com](mailto:soporte@neihec.com)
- 🌐 **Project Portal:** [github.com/hemaguza/k8flow](https://github.com/hemaguza/k8flow)

---

## ☕ Support the Project & Donations

If K8Flow helps you manage your Kubernetes infrastructure or saves your team time, consider supporting ongoing development:

<div align="center">

[![Donate with PayPal](https://img.shields.io/badge/Donate-PayPal-00457C?style=for-the-badge&logo=paypal&logoColor=white)](https://www.paypal.com/donate/?hosted_button_id=4S4KNWJPNR6YL)
[![GitHub Sponsors](https://img.shields.io/badge/Sponsor-GitHub_Sponsors-EA4AAA?style=for-the-badge&logo=github-sponsors&logoColor=white)](https://github.com/sponsors/hemaguza)

<p>Your support directly funds cloud infrastructure testing, new integrations, and FlowBot AI enhancements.</p>

</div>

---

## 🛡️ License & Copyright

Copyright © 2026 **Neihec**. Created and maintained by **[hemaguza](https://github.com/hemaguza)**. All rights reserved.
Distributed for cloud-native infrastructure automation.
