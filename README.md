# Kubernetes Workshop on Huawei Cloud

[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Kubernetes](https://img.shields.io/badge/Kubernetes-1.28+-blue.svg)](https://kubernetes.io)
[![CCE](https://img.shields.io/badge/CCE-Huawei%20Cloud-green.svg)](https://www.huaweicloud.com/)

[中文版](./README.cn.md)

## Introduction

A hands-on Kubernetes workshop based on Huawei Cloud CCE, providing a complete guide to creating, managing, and scaling Kubernetes clusters on Huawei Cloud.

## Table of Contents

- [Architecture](#architecture)
- [Highlights](#highlights)
- [Cloud Services](#cloud-services)
- [Prerequisites](#prerequisites)
- [Quick Start](#quick-start)
- [Usage](#usage)
- [Cleanup](#cleanup)
- [Workshop Modules](#workshop-modules)
- [License](#license)
- [Contact](#contact)

## Architecture
## Workshop Modules

This repository contains 5 self-paced learning paths, fully adapted to Huawei Cloud CCE:

| Path | Content | Modules |
|------|---------|---------|
| 01-path-basics | Basics: environment setup, first cluster, core concepts | 101 Setup / 102 First cluster / 103 Kubernetes concepts |
| 02-path-working-with-clusters | Cluster operations: monitoring, service mesh, upgrades, logging, autoscaling, IaC | 201 Monitoring / 202 Service mesh / 203 Upgrades / 204 EFK logging / 205 Autoscaling / 206 RFS+Terraform / 207 Datadog |
| 03-path-application-development | App development: deploy, discovery, updates, scaling, tracing, Helm, CI/CD, chaos engineering | Modules 301-311 |
| 04-path-security-and-networking | Security & networking: config & secrets, auth, admission policy, network policies, Ingress, CoreDNS | Modules 401-406 |
| 05-path-next-steps | Next steps: best practices & further reading | 501 / 502 |

> Module entry point: `docs/<path-dir>/<module-id-name>/readme.adoc`
> Labs that rely on vendor-specific components without a direct Huawei Cloud counterpart have been replaced with Huawei Cloud solutions or adaptation notes.


```
┌─────────────────────────────────────────────┐
│              Huawei Cloud CCE               │
├─────────────────────────────────────────────┤
│  Kubernetes Cluster                         │
│  ├── Master Nodes                           │
│  ├── Worker Nodes                           │
│  ├── CCE Storage (EVS)                      │
│  └── Networking (VPC/ELB)                   │
├─────────────────────────────────────────────┤
│  Supporting Services                        │
│  ├── OBS (Object Storage)                   │
│  ├── RDS (Database)                         │
│  ├── SWR (Container Images)                 │
│  └── CES/LTS (Monitoring & Logs)            │
└─────────────────────────────────────────────┘
```

## Highlights

- **Cloud Native**: Built on Kubernetes standards
- **Step-by-step**: Lab-style guided modules
- **Hands-on**: Real-world scenario exercises
- **Huawei Cloud Features**: Showcases CCE-specific capabilities

## Cloud Services

| Service | Settlement |
|---------|------------|
| CCE Cluster | By spec |
| CCE Nodes | On-demand |
| OBS | Per storage volume |
| RDS | Monthly subscription |
| ELB | By spec |

## Prerequisites

1. Huawei Cloud account
2. kubectl installed
3. Huawei Cloud CLI (oc) installed
4. Helm installed

## Quick Start

```bash
# 1. Install Huawei Cloud CLI
curl -sSL https://support.huaweicloud.com/cli/inst/oc_tool_install.html | bash

# 2. Configure credentials
oc config set-region cn-north-4

# 3. Create a CCE cluster
oc cce cluster create my-cluster

# 4. Fetch cluster credentials
oc cce cluster config my-cluster

# 5. Verify connectivity
kubectl get nodes
```

## Usage

### Basic Operations

```bash
# List nodes
kubectl get nodes

# List pods
kubectl get pods -A

# Deploy an application
kubectl apply -f deployment.yaml

# Scale a deployment
kubectl scale deployment my-app --replicas=3
```

### Storage Management

```bash
# Create a PV
kubectl apply -f pv.yaml

# Create a PVC
kubectl apply -f pvc.yaml
```

## Cleanup

```bash
# Delete the cluster
oc cce cluster delete my-cluster

# Delete resources
kubectl delete -f deployment.yaml
```

## Workshop Modules

| Module | Content |
|--------|---------|
| Basics | Kubernetes concepts, kubectl fundamentals |
| Cluster Management | CCE cluster creation, node management |
| Application Deployment | Deployment, Service, Ingress |
| Storage | PV, PVC, OBS |
| Networking | Service, Ingress, network policies |
| Security | RBAC, Secret, ConfigMap |
| Monitoring | CES metrics, LTS logs |

## License

MIT License — see the [LICENSE](LICENSE) file for details.

## Contact

- Maintainer: Huawei Cloud Architecture Team
- Email: cloud-architecture@huaweicloud.com
