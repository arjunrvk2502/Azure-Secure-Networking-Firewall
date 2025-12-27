# Azure-Secure-Networking-Firewall
Secure Azure VNet architecture with Firewall (Basic), Bastion Host, DNAT rules, and NGINX-hosted portfolio — no public IPs exposed. Built for security, clarity, and cost-efficiency
# Azure Secure Networking Firewall

This project demonstrates a secure Azure Virtual Network architecture using:

- 🔥 Azure Firewall (Basic SKU)
- 🛡️ Azure Bastion Host
- 🌐 DNAT rules for controlled external access
- 📦 Ubuntu VM running NGINX to host a portfolio site
- 🚫 No public IPs assigned to any VM

---

## 🔧 Architecture Overview

- VNet with three subnets:
  - `AzureFirewallSubnet`
  - `AzureBastionSubnet`
  - `WebSubnet` (for VM)
- Azure Firewall handles inbound traffic via DNAT
- Bastion provides secure SSH/RDP access to the VM
- NSGs restrict traffic between subnets
- NGINX serves a static portfolio site from the VM

---

## 🛠️ Technologies Used

- Azure Virtual Network (VNet)
- Azure Firewall (Basic)
- Azure Bastion
- Network Security Groups (NSGs)
- DNAT Rules
- Ubuntu VM + NGINX
- GitHub for documentation and sharing

---

## 🚀 Setup Instructions

See [`azure-deploy-notes.md`](azure-deploy-notes.md) for full deployment steps including:
- VNet and subnet creation
- Firewall and Bastion setup
- DNAT rule configuration
- NGINX installation [`nginx-install.md`](nginx-install.md)
---

## 📸 Demo

Access the portfolio via:
- http://<Firewall-Public-IP>:8080

---

## 📁 Repository Contents

- `index.html` — Portfolio landing page
- `azure-deploy-notes.md` — Step-by-step deployment guide
- `nginx.conf` — Custom NGINX configuration

---

## 👤 Author

**Arjun Vijayakumar**  
Cloud Engineer | DevOps Engineer | Security Enthusiast 
[LinkedIn](https://www.linkedin.com/in/arjun-vijayakumar-a5609932a)

---

## 🧠 Notes

- Azure Firewall Basic is cost-effective 
- DNAT and Firewall Policy are included at no extra cost
- No public IPs used — all access is routed securely

---

## 📢 Feedback & Collaboration

Feel free to fork, star, or open issues.  
I welcome feedback from fellow cloud engineers and security enthusiasts!
