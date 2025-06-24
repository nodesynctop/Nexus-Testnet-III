# Nexus-Testnet-III
## 🚀 Nexus Testnet CLI Node Setup Guide

### 1. 🔐 Login to Nexus Dashboard
Visit: https://app.nexus.xyz/nodes

Login using:

Your email (you'll receive a secure login link)

Or your Web3 wallet (e.g., MetaMask)

After logging in, click "Add CLI Node"

Copy your Node ID (a numeric value like 345677)

### 2. 🛠️ Run the Setup Script
On your server, run the following command to automatically install and configure the CLI node:
```
bash <(curl -s https://raw.githubusercontent.com/nodesynctop/Nexus-Testnet-III/refs/heads/main/nexus_setup.sh)
```
### 3. ✅ Verify Node Status
Check status:
```
sudo systemctl status nexus
```
Check logs:
```
journalctl -fu nexus -o cat
```
### 4. Remove Nexus Node
```
sudo systemctl stop nexus
sudo systemctl disable nexus
sudo rm /etc/systemd/system/nexus.service
sudo systemctl daemon-reload
sudo rm /usr/local/bin/nexus-network
rm -rf ~/nexus-cli
```
