# Project02-Centralized Network Authentication and Logging using FreeRADIUS, MariaDB, and Rsyslog

This project stores a **Network Project :Centralized Network Authentication and Logging using FreeRADIUS, MariaDB, and Rsyslog** built with **Proxmox + EVE-NG**.  
It includes files for topology, backups , configuration, documentation

The project is organized into 4 main folders

---

## 📂 Folder Structure

### 🔹 `topology/`
- Stores **EVE-NG lab topology files**  
- Includes:
  -  Project 02 - Centralized Network Authentication and Logging using FreeRADIUS MariaDB and Rsys.zip 

- Each `.unl` file on `.zip` defines:
  - Nodes (Firewall, switches, vPC , vServers)  
  - Images used (Cisco IOSv, Fortinet7.0, vPC , vServer)  
  - Resource settings (CPU, RAM, interfaces)  
  - Network connections between devices  

- Used to quickly import the full network design into **EVE-NG** and recreate the lab environment

---

### 🔹 `backups/`
- Contains **system-level backup files** used in this lab  
- Includes:
  - `Firewall/` 
    - `FGT-HQ_7-0_0066_202509241120.conf`

- Used for restoring actual systems (VMs or devices)

---

### 🔹 `configs/`
- Contains **text-based configuration files** of devices in this lab  
- Includes:
  - `Switch/` (Cisco Switch configuration) 
    - `Distribution_DCSW01.cfg`
    - `Distribution_DCSW02.cfg`      

- Easy to read/edit and allows tracking changes with Git


---

### 🔹 `docs/`
- Contains **documentation and test evidence** for this lab  
- Includes:
  - `Network Diagram Centralized Network Authentication and Logging using FreeRADIUS MariaDB and Rsyslog.png` → Diagram or Network Topology  
  - `test_result.md` → Test results with screenshots/logs  

- Used for reference and to showcase as a portfolio

---

## 🚀 How to Use
1. Import the topology file (`.zip`) into EVE-NG Load from `docs/`
2. Load Backup Configuration Fortinet for Restore from the `backups/Firewall/` 
3. Load configurations from the `configs/` folder into the devices vISP , SwitchsHQ and SwitchsDC
4. Review `docs/test_result.md` for actual test results  

---
