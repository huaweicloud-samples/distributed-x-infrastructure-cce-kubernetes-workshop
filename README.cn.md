# Kubernetes 华为云 Workshop

[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Kubernetes](https://img.shields.io/badge/Kubernetes-1.28+-blue.svg)](https://kubernetes.io)
[![CCE](https://img.shields.io/badge/CCE-华为云-green.svg)](https://www.huaweicloud.com/)

[English](./README.md)

## 简介

基于华为云 CCE 的 Kubernetes Workshop 教程，提供在华为云上创建、管理和扩展 Kubernetes 集群的完整指南。

## 目录

- [架构图](#架构图)
- [方案亮点](#方案亮点)
- [涉及云服务](#涉及云服务)
- [前置条件](#前置条件)
- [快速开始](#快速开始)
- [使用方法](#使用方法)
- [清理资源](#清理资源)
- [详细说明](#详细说明)
- [许可证](#许可证)
- [联系方式](#联系方式)

## 架构图
## 教程模块

本仓库包含 5 条自定进学习路径，全部适配华为云 CCE：

| 路径 | 内容 | 模块 |
|------|------|------|
| 01-path-basics | 入门：环境准备、首个集群、核心概念 | 101 环境准备 / 102 创建集群 / 103 Kubernetes 概念 |
| 02-path-working-with-clusters | 集群运维：监控、服务网格、升级、日志、伸缩、IaC | 201 监控 / 202 服务网格 / 203 升级 / 204 EFK 日志 / 205 自动伸缩 / 206 RFS+Terraform / 207 Datadog 监控 |
| 03-path-application-development | 应用开发：部署、发现、更新、伸缩、追踪、Helm、CI/CD、混沌工程 | 301-311 共 11 个模块 |
| 04-path-security-and-networking | 安全与网络：配置与密钥、认证授权、准入策略、网络策略、Ingress、CoreDNS | 401-406 共 6 个模块 |
| 05-path-next-steps | 进阶：最佳实践与延伸阅读 | 501 / 502 |

> 各模块入口：`docs/<路径目录>/<模块号-名称>/readme.adoc`
> 依赖特定厂商组件、在华为云上无直接对应物的实验，已替换为华为云方案或改写为适配说明。


```
┌─────────────────────────────────────────────┐
│              华为云 CCE                      │
├─────────────────────────────────────────────┤
│  Kubernetes 集群                          │
│  ├── Master Nodes (管理节点)              │
│  ├── Worker Nodes (工作节点)              │
│  ├── CCE 存储 (EVS)                       │
│  └── 网络 (VPC/ELB)                     │
├─────────────────────────────────────────────┤
│  配套服务                                 │
│  ├── OBS (对象存储)                       │
│  ├── RDS (数据库)                        │
│  ├── SWR (容器镜像)                      │
│  └── CES/LTS (监控日志)                  │
└─────────────────────────────────────────────┘
```

## 方案亮点

- **云原生**：基于 Kubernetes 标准
- **手把手教程**：分步骤实验室形式
- **实践性强**：包含真实场景练习
- **华为云特性**：展示 CCE 特有功能

## 涉及云服务

| 云服务 | 结算方式 |
|--------|----------|
| CCE 集群 | 按规格 |
| CCE 节点 | 按需 |
| OBS | 按存储量结算 |
| RDS | 包年包月 |
| ELB | 按规格 |

## 前置条件

1. 华为云账号
2. 安装 kubectl
3. 安装华为云 CLI (oc)
4. 安装 Helm

## 快速开始

```bash
# 1. 安装华为云 CLI
curl -sSL https://support.huaweicloud.com/cli/inst/oc_tool_install.html | bash

# 2. 配置凭据
oc config set-region cn-north-4

# 3. 创建 CCE 集群
oc cce cluster create my-cluster

# 4. 获取集群凭证
oc cce cluster config my-cluster

# 5. 验证连接
kubectl get nodes
```

## 使用方法

### 基础操作

```bash
# 查看节点
kubectl get nodes

# 查看 Pod
kubectl get pods -A

# 部署应用
kubectl apply -f deployment.yaml

# 扩缩容
kubectl scale deployment my-app --replicas=3
```

### 存储管理

```bash
# 创建 PV
kubectl apply -f pv.yaml

# 创建 PVC
kubectl apply -f pvc.yaml
```

## 清理资源

```bash
# 删除集群
oc cce cluster delete my-cluster

# 删除资源
kubectl delete -f deployment.yaml
```

## 详细说明

### 教程模块

| 模块 | 内容 |
|------|------|
| 基础 | Kubernetes 概念、kubectl 基础 |
| 集群管理 | CCE 集群创建、节点管理 |
| 应用部署 | Deployment、Service、Ingress |
| 存储 | PV、PVC、OBS |
| 网络 | Service、Ingress，网络策略 |
| 安全 | RBAC、Secret、ConfigMap |
| 监控 | CES 指标、LTS 日志 |

## 许可证

MIT License - 详见 [LICENSE](LICENSE) 文件

## 联系方式

- 维护者：华为云架构团队
- 邮箱：cloud-architecture@huaweicloud.com
