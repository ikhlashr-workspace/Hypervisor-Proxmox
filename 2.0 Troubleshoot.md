
# Proxmox unauthorized IP .... when APT Update/upgrade/installing system ( Enterprise )

## 🔹 1. Check Repository List
Ensure that the correct repository is configured for Proxmox. Run the following commands to check the current repositories:

```bash
cat /etc/apt/sources.list
cat /etc/apt/sources.list.d/*
```

Make sure only the following repositories are present for **Proxmox (No Subscription)**:

```nginx
deb http://download.proxmox.com/debian/pve bookworm pve-no-subscription
deb http://deb.debian.org/debian bookworm main contrib
deb http://security.debian.org/ bookworm-security main contrib
deb http://deb.debian.org/debian bookworm-updates main contrib
```

If any **enterprise** repository is present, **remove or comment it out** by adding `#` at the beginning of the line.

---

## 🔹 2. Clear APT Cache & Update
Run the following commands to clear the cache and refresh the package list:

```bash
apt-get clean
rm -rf /var/lib/apt/lists/*
apt-get update
```

If errors persist, force the update with:

```bash
apt-get update --allow-releaseinfo-change
```

---

## 🔹 3. Use a Mirror Repository
If Proxmox's main repository is **down or slow**, use a mirror repository.

1. Open the repository list:

   ```bash
   nano /etc/apt/sources.list.d/pve-no-subscription.list
   ```

2. Replace the contents with the following mirror repositories:

   ```nginx
   deb http://mirror.hetzner.com/debian/packages bookworm main contrib
   deb http://mirror.hetzner.com/debian/security bookworm-security main contrib
   deb http://mirror.hetzner.com/debian/packages bookworm-updates main contrib
   deb http://mirror.hetzner.com/proxmox/debian/pve bookworm pve-no-subscription
   ```

3. Save the file (`CTRL+X`, then `Y`, then `ENTER`).

4. Update the package list again:

   ```bash
   apt-get update
   ```

✅ Your Proxmox repository should now be correctly configured and working!
