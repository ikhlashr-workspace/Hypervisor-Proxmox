# 🚀 Enabling Wi-Fi on Proxmox VE

## ⚠️ Default Proxmox Does Not Support Wi-Fi
By default, **Proxmox VE does not provide built-in support for Wi-Fi**, as it is designed for server environments that typically use **wired (LAN) connections**. However, if you need to connect Proxmox to a Wi-Fi network, follow the steps below to manually set up Wi-Fi.

---

## 📌 Step-by-Step Wi-Fi Setup on Proxmox

### 1️⃣ Install Wi-Fi Software
Update package lists and install the required Wi-Fi tools:
```bash
apt update
apt install wireless-tools wpasupplicant iw -y
```

### 2️⃣ Scan Available Wi-Fi Networks
Find the available Wi-Fi networks using:
```bash
iwlist wlp3s0 scan | grep ESSID
```
Replace `wlp3s0` with your Wi-Fi interface name (check with `ip a`).

### 3️⃣ Manually Configure Wi-Fi Connection
Create a configuration file for Wi-Fi:
```bash
nano /etc/wpa_supplicant/wpa_supplicant.conf
```
Add the following lines (replace with your SSID and password):
```bash
network={
    ssid="SSID_WIFI"
    psk="PASSWORD_WIFI"
    key_mgmt=WPA-PSK
}
```
Save the file (`CTRL + X`, then `Y` to confirm).

### 4️⃣ Connect Wi-Fi to Network
Run the following commands to connect to Wi-Fi:
```bash
wpa_supplicant -B -i wlp3s0 -c /etc/wpa_supplicant/wpa_supplicant.conf
dhclient wlp3s0
```

### ✅ Verify the Connection
Check if Wi-Fi is successfully connected:
```bash
ip a show wlp3s0
```
Or, test connectivity by pinging Google:
```bash
ping -c 4 8.8.8.8
```

---

## 📝 Notes
- Replace `wlp3s0` with your actual Wi-Fi interface name.
- If `dhclient` is not found, install it with `apt install isc-dhcp-client -y`.
- For persistent Wi-Fi connection, consider configuring `/etc/network/interfaces`.

🎯 Now your **Proxmox VE** is connected to Wi-Fi! 🚀
