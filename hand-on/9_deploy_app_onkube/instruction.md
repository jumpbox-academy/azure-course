# Deploy application

1. Get your kubecontext

```bash
az aks get-credentials -n <cluster_name> -g <cluster_resource_group_name>
```

2. Check the connection

```bash
kubectl get node
```

output must like this

```plain
NAME                                STATUS   ROLES    AGE   VERSION
aks-agentpool-26276286-vmss000004   Ready    <none>   64m   v1.29.5
aks-agentpool-26276286-vmss000005   Ready    <none>   64m   v1.29.5
```

3. Apply manifest files

```bash
# You muse be in folder "./hand-on/9_deploy_app_onkube/manifest" first.
kubectl apply -f ns
kubectl apply -f micro-1
kubectl apply -f micro-2
```

## Additional

install nginx ingres

```bash
# You muse be in folder "./hand-on/9_deploy_app_onkube/helm_values" first.
helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
helm install nginx ingress-nginx/ingress-nginx --version 4.11.1 -n nginx-ingress -f nginx-ingress.yaml

# or

helm upgrade nginx ingress-nginx/ingress-nginx --version 4.11.1 -n nginx-ingress -f nginx-ingress.yaml
```

---

## Network test pod

You can directly create pod and remote into it for network inspection inside the cluster.

```bash
kubectl run -it --image ubuntu:22.04 test-net -- bash
apt update && apt install curl -y
curl https://ifconfig.me # check your ip
```
