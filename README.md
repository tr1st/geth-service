# geth-service

1. Create an `start-geth.sh` file with execution rights

```
geth --http --http.port 8545 --mine --miner.threads=0 --cache=16384
```

```
chmod +x start-geth.sh
```

2. Install geth.service to `/lib/systemd/system/geth.service` with a valid path to start-geth.sh

```
[Unit]
Description=Ethereum go client
[Service]
User=[USER]
Type=simple
WorkingDirectory=/home/[USER]
ExecStart=/bin/bash /home/[USER]/start-geth.sh
Restart=on-failure
RestartSec=5
[Install]
WantedBy=default.target
```

3. Enable service

```
systemctl enable geth.service
```
