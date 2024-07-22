# VM section instruction

Before do this instruction, check you have already created VNet.

Placeholder variable name with `<var_name>`

1. Create VM from portal

   spec

   ```text
   Subscription: any
   resouce-group: <org>-rg-sbx
   vm-name: <org>-blue-vm-sbx
   image: ubuntu:22.04 LTS - x64 Gen2
   size: Standard_B1s
   arch: x64
   Security-type: vTPM
   zone: 2
   ssh-key: use existing key or gen a new one
   username: azureuser
   public-inbound-ports: ssh(22)
   disk:
    os:
      size: 30gb
      type: standard ssd (LRS)
      delete-with-vm: true
   network:
    subnet: as your prefer
    public-ip: <org>-blue-ip-sbx
    delete-public-ip-and-nic-when-delete: true
    NIC-sg: <org>-blue-sg-sbx
   management:
    enable-system-assign-managed-identity: true
   monitoring:
    boot-diagnostics: disable for now
   extension:
    - ms entra id ssh login
   ```

   user-data:

   ```bash
      #!/bin/bash

      echo "hello world" >> foo.log
      echo "$(whoami)" >> foo.log

   ```

   Note: this script will run as `root` at path `/`

2. Role Assignment to your account with role `Virtual Machine Administrator Login`
