# Create Log workspace

1. Create log workspace

   ```yaml
   spec:
     name: <org>-law-redlab-sbx-sea
     region: as same as rg
     resouce-group: <org>-rg-demo-sbx-<region>
   ```

2. Create Data collection endpoint

   For vm, create from log menu in vm page

   ```yaml
   spec:
     name: <org>-mg-redlab-sbx-sea
     region: as same as rg
   ```
