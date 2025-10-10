# 📘 Documentation of Each Project Folder

This Folder Projects contains **Network lab projects** built on **Proxmox VE** and **EVE-NG**,  
focusing on enterprise network design, security, and VPN deployment.  

---

### 🔹 Project 01 – Hierarchical Network Design with Cisco vIOS and Fortinet Next-Gen Firewall
**Lab Environment:** Proxmox VE + EVE-NG  
- Designed a **Hierarchical network architecture** (Core–Distribution–Access)  
- Integrated Cisco L2/L3 switches  and Fortinet next-gen firewall
- Configured:
  - **Firewall Policys** for network security by fortinets
  - **Redundant links** for high Availability links
  - **OSPF** dynamic routing & default static route  
  - **VLANs** for segmentation  
  - **VRRP** for high availability  
  - **RSTP with Root Guard** for loop prevention  
  - **Root Bridge**
  - **spanning-tree guard root** and **spanning-tree portfast, spanning-tree bpduguard enable, port-security**
  - **DHCP servers** on distribution switchs

<!-- ---

### 🔹 Project 02 – Centralized Network Authentication and Logging using FreeRADIUS, MariaDB, and Rsyslog
**Lab Environment:** Proxmox VE + EVE-NG  
- Implemented 802.1X network authentication using FreeRADIUS integrated with MariaDB for centralized user credential storage.
- Configured Rsyslog to collect authentication and accounting logs from FreeRADIUS, Cisco Switch, and Fortinet Firewall. -->

---

### 🔹 Project 02 – IPsec Site-to-Site VPN Deployment with Fortinet
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