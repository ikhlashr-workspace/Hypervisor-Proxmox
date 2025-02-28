# 🔐 Accessing Proxmox via SSH or Web UI

## 1️⃣ Accessing Proxmox Web UI
Proxmox provides a web-based management interface that can be accessed through a browser. To access it:

1. Open your browser.
2. Navigate to:
   ```
   https://<your-proxmox-ip>:8006
   ```
3. Log in using your **root** credentials.

📌 **Note:** If you encounter a security warning, proceed by accepting the self-signed SSL certificate.
![image](https://github.com/user-attachments/assets/b529b934-2c85-4c58-b8cd-47917342b8a9)

## 2️⃣ Accessing Proxmox via SSH
To manage Proxmox via **SSH**, follow these steps:

1. Open a terminal (Linux/macOS) or use PuTTY (Windows).
2. Connect using SSH:
   ```bash
   ssh root@<your-proxmox-ip>
   ```
3. Enter your **root** password when prompted.

✅ Once connected, you can manage Proxmox via the command line.
![image](https://github.com/user-attachments/assets/9d4e9ecb-ce04-449b-b556-152ecf7cc09e)

## 🛠️ Troubleshooting
- Ensure that **SSH service** is running:
  ```bash
  systemctl status ssh
  ```
  ![image](https://github.com/user-attachments/assets/63ea0ff8-4c93-4401-ab54-28353f4322f4)

- If the web UI is inaccessible, restart the Proxmox web service:
  ```bash
  systemctl restart pveproxy
  ```
- Verify Proxmox IP address with:
  ```bash
  ip a
  ```

🎯 Now you can access **Proxmox VE** via Web UI or SSH! 🚀
