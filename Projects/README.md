# 📘 Documentation of Each Project Folder

This Folder Projects contains **Network lab projects** built on **Proxmox VE** and **EVE-NG**,  
focusing on enterprise network design, security, and VPN deployment.  

---

### 🔹 Project 01 – Hierarchical Network Design with Cisco vIOS
**Lab Environment:** Proxmox VE + EVE-NG  
- Designed a **Hierarchical network architecture** (Core–Distribution–Access)  
- Integrated Cisco L2/L3 switches  
- Configured:
  - **OSPF** dynamic routing & default static route  
  - **VLANs** for segmentation  
  - **VRRP** for high availability  
  - **RSTP with Root Guard** for loop prevention  
  - **DHCP Spoofing protection** and **DHCP Relay**  

---

### 🔹 Project 02 – Enterprise Network Security (Cisco vIOS + AD + FreeRADIUS + Graylog)
**Lab Environment:** Proxmox VE + EVE-NG  
- Integrated **CISCO vIOS**, **Microsoft Active Directory**, **FreeRADIUS** and **Graylog**
- Configured **LDAP + RADIUS authentication** for secure network access  
- Deployed centralized **AAA framework with 802.1X authentication**  
- Integrated **Graylog** for centralized logging, monitoring, and analysis  

---

### 🔹 Project 03 – IPsec Site-to-Site VPN Deployment with Fortinet
**Lab Environment:** Proxmox VE + EVE-NG  
- Designed a **secure VPN topology** connecting **Branch ↔ HQ between Data Center**  
- Configured **Fortinet** for IPsec Site-to-Site VPN tunnels  
- Verified encrypted communication and remote site connectivity  

---

## ✨ Notes
- Each project folder contains:
  - `backups/` → VM & device backups link backup files(e.g.,Proxmox ) be stored externally Google Drive.
  - `configs/` → Text-based configurations  
  - `docs/` → Diagrams, test plans, and results  
  - `topology/` → EVE-NG `.unl` files and diagrams  