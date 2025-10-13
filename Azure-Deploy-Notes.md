# Azure Secure Networking — Deployment Guide

This guide walks through deploying a secure Azure VNet architecture with Firewall (Basic), Bastion, DNAT, and a private VM running NGINX — all without exposing public IPs.

---

## 1. Network Architecture

- **VNet Name**: `secure-vnet`
- **Subnets**:
  - `AzureFirewallSubnet` — required for Azure Firewall
  - `AzureBastionSubnet` — required for Bastion Host
  - `WebSubnet` — hosts the Ubuntu VM

---

## 2. Deploy Azure Firewall (Basic SKU)

- Create Azure Firewall in `AzureFirewallSubnet`
- Assign a **static public IP**
- Create a **DNAT rule**:
  - **Source**: `Your IP` (Any)
  - **Destination**: Firewall Public IP
  - **Port**: `8080`
  - **Translated Address**: VM Private IP
  - **Translated Port**: `80`
- Associate a **Firewall Policy** (Basic tier includes this)

---

## 3. Deploy Azure Bastion

- Create Bastion in `AzureBastionSubnet`
- Use for secure SSH/RDP access to the VM
- No public IP needed on the VM

---

## 4. Deploy Ubuntu VM

- Place VM in `WebSubnet`
- **No public IP**
- Use Bastion to SSH into the VM

---

## 5. Install and Configure NGINX

- Follow the steps in nginx-install.md


6. Configure NSG
- Attach NSG to WebSubnet or VM NIC
- Inbound rules:
- ✅ Allow port 80 from Firewall Private IP
- ✅ Allow SSH (22) from Azure Bastion
- ❌ Deny all other inbound traffic

7. Test Access
- Open browser and visit:
http://<Firewall-Public-IP>:8080


- You should see your custom portfolio page served by NGINX
