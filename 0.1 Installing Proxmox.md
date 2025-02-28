# 🖥️ Proxmox VE: Installation & Architecture Guide

## 🏗️ Infrastructure Requirements
| Component | Minimum Requirement | Recommended for Production |
|-----------|---------------------|---------------------------|
| **CPU** | 64-bit processor with VT-x/AMD-V | Intel Xeon / AMD EPYC |
| **RAM** | 4GB | 32GB+ |
| **Storage** | 20GB SSD | NVMe SSD or RAID |
| **Network** | 1GbE | 10GbE for clustering |

## 🚀 Installing Proxmox VE
### **1️⃣ Download Proxmox ISO**
Download the latest Proxmox VE ISO from the [official website](https://www.proxmox.com/downloads).

### **2️⃣ Create a Bootable USB**
Use **Rufus** (Windows)

![image](https://github.com/user-attachments/assets/d2b9a259-100c-4859-9c00-fb056b5a2752)

### **3️⃣ Boot and Install**
  1. Insert the USB and boot from it.
  2. Follow the installation Wizard:
  3. Select target Disk ( SSD Recommended )
  4. Set Root Password & Admin Email
  5. Configure Network Interface
  6. Click Install and wait for completion

### **NOTES**
🚨 Proxmox and Wi-Fi Connection  
By default, **Proxmox VE does not provide built-in support for Wi-Fi**, as it is designed to run on servers that typically use a **stable LAN (Ethernet) connection**. Therefore, using a **wired (LAN) connection** is highly recommended for the best performance and full compatibility with Proxmox features such as **clustering, storage sharing, and network bridging**.  

However, if you want to use Wi-Fi on Proxmox, you will need to configure it manually. A complete guide on **how to set up Wi-Fi on Proxmox VE** can be found on the following GitHub repository:  

📌 **[[10 Additional Wifi Configuration]](https://github.com/ikhlashr-workspace/Hypervisor-Proxmox/blob/main/10%20Additional%20Wifi%20Configuration.md)** 


Please note that using **Wi-Fi for virtualization and production servers is not recommended**, mainly due to **high latency, network instability, and lower throughput compared to Ethernet**. 🚀  
     
