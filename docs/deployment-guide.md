# 部署指南

## 前置条件

1. 华为云账号
2. 安装 kubectl
3. 安装华为云 CLI (oc)
4. 安装 Helm

## 部署步骤

### 1. 安装 CLI 工具

```bash
# 安装 oc CLI
curl -sSL https://support.huaweicloud.com/cli/inst/oc_tool_install.html | bash

# 验证安装
oc version
```

### 2. 配置认证

```bash
# 登录华为云
oc login -u <username> -p <password>
```

### 3. 创建 CCE 集群

```bash
# 查看可用规格
oc cce flavors

# 创建集群
oc cce cluster create my-cluster \
  --flavor cce.s1.medium \
  --version v1.28 \
  --vpc my-vpc \
  --subnet my-subnet
```

### 4. 获取凭证

```bash
# 配置集群凭证
oc cce cluster config my-cluster

# 验证连接
kubectl get nodes
```

### 5. 部署示例应用

```bash
# 部署 nginx
kubectl create deployment nginx --image=nginx

# 暴露服务
kubectl expose deployment nginx --port=80 --type=LoadBalancer
```

## 资源清单

| 资源类型 | 说明 |
|----------|------|
| CCE 集群 | 1 个 |
| 节点 | 根据配置 |
| ELB | 按需 |
| OBS | 按需 |

## 清理

```bash
# 删除集群
oc cce cluster delete my-cluster

# 或通过控制台删除
```
