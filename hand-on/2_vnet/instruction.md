# Create Vnet

1. Create Resource group

   ```yaml
   name: <org>-rg-demo-sbx-<region>
   region: as your prefer.
   ```

2. Create vnet for vm with this spec

```yaml
spec:
  name: <org>-vnet-demo-sbx-<region>
  resource-group: <org>-rg-demo-sbx-<region>
  address-space: "10.224.0.0/12"
  subnets:
    - name: snet-general-1
      address-prefixs: "10.224.0.0/24"
    - name: snet-vm-1
      address-prefixs: "10.225.0.0/16"
    - name: "snet-aks-1"
      address-prefixs: ""10.226.0.0/16""
```
