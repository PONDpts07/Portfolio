# Project01 – Hirechical Network Design with Cisco vIOS and Configure

This project stores a **Network Project Hirechical Network Design with Cisco vIOS and Configure** built with **Proxmox + EVE-NG**.  
It includes files for topology, backups , configuration, documentation

The project is organized into 4 main folders

---

## 📂 Folder Structure

### 🔹 `topology/`
- Stores **EVE-NG lab topology files**  
- Includes:
  - `lab1.unl` (EVE-NG lab file in XML format)  

- Each `.unl` file defines:
  - Nodes (routers, switches, servers, etc.)  
  - Images used (Cisco IOSv, Linux, vPC etc.)  
  - Resource settings (CPU, RAM, interfaces)  
  - Network connections between devices  

- Used to quickly import the full network design into **EVE-NG** and recreate the lab environment

---

### 🔹 `backups/`
- Contains **system-level backup files** used in this lab  
- Includes:
  - Proxmox VM backup (`.conf`, `.vma.zst`)  
  - Routers/Switch backup (`.conf`, `.backup`, `.rsc`)  

- Each Folders in Google Drive:
  - r1.conf

- Used for restoring actual systems (VMs or devices)
- Large backup files (e.g., Proxmox `.vma.zst`) be stored externally (Google Drive) with a link provided in File backups.md

---

### 🔹 `configs/`
- Contains **text-based configuration files** of devices in this lab  
- Includes:
  - R1.cfg (Cisco Router configuration)  
  - SW1.cfg (Cisco Switch configuration)  
- Easy to read/edit and allows tracking changes with Git


---

### 🔹 `docs/`
- Contains **documentation and test evidence** for this lab  
- Includes:
  - `design_diagram.png` → Diagram or Network Topology  
  - `test_plan.md` → Test cases / scenarios  
  - `test_result.md` → Test results with screenshots/logs  
- Used for reference and to showcase as a portfolio

---

## 🚀 How to Use
1. Import the topology file (`.unl`) into EVE-NG  
2. Load configurations from the `configs/` folder into the devices  
3. To restore actual VMs  → use files from `backups/`  
4. Check `docs/test_plan.md` for the testing procedure  
5. Review `docs/test_result.md` for actual test results  

---

## ✨ Notes
- This repository is intended as a **Reference/Portfolio**  
