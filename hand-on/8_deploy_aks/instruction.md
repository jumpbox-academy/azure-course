# Deploy AKS

1. Create AKS with this spec

```yaml
spec:
  name: <org>-aks-redlab-sbx
  resource-group: as you prefer
  cluster-preset-config: Dev/Test
  region: same as rg
  availbability-zones:
    - 2
  aks-price-tier: free
  kubernetes-version: 1.29.5
  authn-authz: Microsoft entra id auth with azure RBAC
  node-pools:
    agentpool:
      mode: system
      OS-SKU: azure-linux
      az:
        - 2
      node-size: D2as
      scale-method: autoscale
      min-node: 1
      max-node: 3
      max-pod-per-node: 40
    workload1:
      mode: system
      OS-SKU: azure-linux
      az:
        - 2
      node-size: D2as
      scale-method: autoscale
      min-node: 0
      max-node: 3
      max-pod-per-node: 40
  network:
    enable-private-cluster: public/private
    network-config: azure CNI overlay
    dns-name-prefix: <org>-aks-redlab-sbx
    enable-cilium: true
    bring-your-own-vnet: true
    vnet: as you prefer
    subnet: as you prefer
    kube-service-addr-rangd: 10.16.0.0/16
    kube-dns-svc-ip: "10.16.0.10"
    load-balance: standard
  integrations: {}
  monitoring:
    enable-container-logs: true
    log-analytics-workspace: as you prefer
    cost-preset: standard
    enable-recommended-alert-rules: true
```

2. Get kube context into your PC

```bash
az aks get-credentials --resource-group myResourceGroup --name myAKSCluster
```

3. Test with kubectl

```bash
kubectl get node
```
