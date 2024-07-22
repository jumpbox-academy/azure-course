# Create NSG

1. Create nsg

   make sure you nsg rules is created following this:

   ```yaml
   inbound:
     allowSSH:
       port: 22
       protocol: tcp
       source: any
       destination: any
     allowICMP:
       port: 0
       protocol: icmpV4
       source: any
       destination: any
   outbound:
     allowHttp:
       port: 80
       protocol: tcp
       source: any
       destination: any
     allowHttps:
       port: 443
       protocol: tcp
       source: any
       destination: any
   ```

2. Attach Network security group to network interface of the vm
