# Project01 – Hirechical Network Design with Cisco vIOS and Fortinet Next-Gen Firewall

This project stores a **Network Project : HHierarchical Network Design with Cisco vIOS and Fortinet Next-Gen Firewall** built with **Proxmox + EVE-NG**.  
It includes files for topology, backups , configuration, documentation

The project is organized into 4 main folders

---

## 📂 Folder Structure

### 🔹 `topology/`
- Stores **EVE-NG lab topology files**  
- Includes:
  -  Project 01 - Hierarchical Network Design.zip 

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
    - `FGT-01_7-0_0066_202509281110.conf`
    - `FGT-02_7-0_0066_202509281110.conf `

- Used for restoring actual systems (VMs or devices)

---

### 🔹 `configs/`
- Contains **text-based configuration files** of devices in this lab  
- Includes:
  - `Router/` (Cisco Router configuration)
    -  `VISP.cfg` 

  - `Switch/` (Cisco Switch configuration) 
    - `Access1.cfg`
    - `Access2.cfg`
    - `Core1.cfg`
    - `Core2.cfg`
    - `Distribution1.cfg`
    - `Distribution2.cfg`      

- Easy to read/edit and allows tracking changes with Git


---

### 🔹 `docs/`
- Contains **documentation and test evidence** for this lab  
- Includes:
  - `Network Diagram  Hierarchical Network.png` → Diagram or Network Topology  
  - `test_result.md` → Test results with screenshots/logs  

- Used for reference and to showcase as a portfolio

---

## 🚀 How to Use
1. Import the topology file (`.zip`) into EVE-NG Load from `docs/`
2. Load Backup Configuration Fortinet for Restore from the `backups/Firewall/` 
3. Load configurations from the `configs/` folder into the devices vISP , Core_Switchs , Distribution_Switchs and Access_Switchs 
4. Review `docs/test_result.md` for actual test results  

---

