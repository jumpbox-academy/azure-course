# Create Storage Account

prerequisite

- already have resources-group

This tutorial shows how to create storage account for log diagnosetics

1. create storage account for log diagnosetics

   ```yaml
   spec:
     name: <org>vmdiagnose
     performance: standard
     region: same as resource-group
     redundancy: LRS
     req-secure-transfer-restapi: true
     enable-storage-account-key-access: true
     min-tls: 1.2
     permited-scope-for-copy: From any storage account
     network:
       network-access:
         public-access-from-selected-vnet-ip: true
         vnet: as your prefer
       route-preference: microsoft-network-routing
     recovery:
       soft-recover-for-blob: 7day
       containers: 7day
       fileshares: 7day
     encrypt:
       type: MMK
       support-customer-managed-keys: all-service
   ```
