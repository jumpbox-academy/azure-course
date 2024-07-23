# Deploy app to vm

Prerequisite

- A VM with public access
- os ubuntu 22.04

1. SSH into your VM that you was created

   ```bash
   az ssh vm -n <vm_name> -g <resource_group_name>
   ```

2. install curl

   ```bash
     sudo apt update && sudo apt install curl -y
   ```

3. download app

   ```bash
     sudo mkdir /app
     sudo chown azureuser:azureuser -R /app
     sudo chmod 755 -R /app
     curl -L https://gitlab.com/puksigon/little-microservice/-/package_files/139559074/download -o /app/little-microservice

   ```

   setup_config

```bash
cat <<EOF > config.yaml
service:
  name: micro-1
apiConfig:
  port: "80"

serviceA:
  enabled: false
  url: "http://little-micro-2:4000/api/ping"
  interval: "5s"
EOF

sudo mv config.yaml /app/config.yaml
```

4. Apply ENV
   SERVICE_NAME: "micro-1"

5. create systemd service

```bash
cat <<EOF > little-micro.service
[Unit]
Description=little-microservice
After=network.target

[Service]
ExecStart=/app/little-microservice
WorkingDirectory=/app
User=root
Group=root

[Install]
WantedBy=multi-user.target
EOF

sudo mv little-micro.service /etc/systemd/system/little-micro.service
sudo systemctl enable little-micro.service
sudo systemctl start little-micro.service
sudo systemctl status little-micro.service
```

If you change `/etc/systemd/system/little-micro.service` file, you need to reload

```bash
sudo systemctl daemon-reload
```

6. See log with journalctl

```bash
sudo journalctl -f -u little-micro.service
```
