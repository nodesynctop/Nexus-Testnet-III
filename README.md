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
![nexus3](https://github.com/user-attachments/assets/13ded2db-152c-43fb-b818-6f0efd9c6266)

#### Option 1: Run directly via curl + bash
```
bash <(curl -s https://raw.githubusercontent.com/nodesynctop/Nexus-Testnet-III/refs/heads/main/nexus_setup.sh)
```
#### Option 2: Download, make executable, then run
```
curl -o nexus_setup.sh https://raw.githubusercontent.com/nodesynctop/Nexus-Testnet-III/refs/heads/main/nexus_setup.sh
chmod +x nexus_setup.sh
./nexus_setup.sh
```
### 3. ✅ Verify Node Status
Check status:
```
sudo systemctl status nexus
```
![nexus3_2](https://github.com/user-attachments/assets/31d8c1b0-5eb2-4c4b-b5d5-af2858d7d5f1)

Check logs:
```
journalctl -fu nexus -o cat
```
### 4. Upgrade VERSION=v0.9.0
```
sudo systemctl stop nexus
cd $HOME/nexus-cli/clients/cli
VERSION=v0.9.0
git fetch --all
git checkout $VERSION
cargo build --release

sudo mv target/release/nexus-network /usr/local/bin/
nexus-network --version

sudo systemctl restart nexus
journalctl -fu nexus -o cat
```
### 5. Remove Nexus Node
```
sudo systemctl stop nexus
sudo systemctl disable nexus
sudo rm /etc/systemd/system/nexus.service
sudo systemctl daemon-reload
sudo rm /usr/local/bin/nexus-network
rm -rf ~/nexus-cli
```
