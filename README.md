# 🚀 Fast Ubuntu 24.04 XFCE Remote Desktop on GitHub Actions

This repository provides an ultra-fast, lightweight, and modern **Ubuntu 24.04 LTS (XFCE4)** cloud desktop accessible from **Mac, Windows, Linux, and Mobile** using 100% free tools (Cloudflare Quick Tunnels, noVNC, and XRDP).

### ✨ Highlights:
- ⚡ **Lightning Fast & Ultra-Snappy**: Consumes only ~350 MB RAM, boots up in under 35 seconds, and has zero input lag over remote sessions.
- 🎨 **Modern Sleek Aesthetics**: Pre-configured with **Arc-Dark Theme** and **Papirus-Dark Icons**.
- 🌐 **Instant Browser Access**: Free **Cloudflare Quick Tunnel** with one-click access (`https://xxxx.trycloudflare.com/vnc.html`) without installing client software.
- 🔌 **Native RDP Support**: Connect using Microsoft Remote Desktop on Windows / Mac via Tailscale or Ngrok.
- ⏱️ **Up to 5.8 Hours** per continuous run (can be re-triggered anytime).

---

## ⚡ Quick Start Guide

### 1. Launch the Desktop Workflow
1. Go to your repository on GitHub.
2. Click on the **Actions** tab.
3. Select **Ubuntu 24.04 XFCE Fast Remote Desktop** from the left sidebar.
4. Click **Run workflow**.
5. *(Optional)* Customize the parameters:
   - **VNC & User Password**: Set a custom password (default: `Admin@12345`).
   - **Screen Resolution**: e.g., `1920x1080`, `2560x1440`, `1366x768`.
   - **Session duration**: Duration in hours (up to `5.5` hrs).
6. Click the green **Run workflow** button.

---

## 🌐 Connecting from Mac / Windows

### Option 1: Web Browser (Instant, Zero Client Setup)
1. In GitHub Actions, click on the active workflow run.
2. Click on the **Summary** tab (or check the step `Launch Cloudflare Quick Tunnel & Extract Access Link`).
3. Open the generated Cloudflare URL (e.g. `https://xxxx.trycloudflare.com/vnc.html`).
4. Enter your password (`Admin@12345`) and click **Connect**.
5. Enjoy your lightning-fast XFCE desktop!

### Option 2: Native Microsoft Remote Desktop (XRDP)
If you prefer the native **Microsoft Remote Desktop** app:
- **Using Tailscale (Recommended for fast, direct, encrypted connection)**:
  - Generate an auth key from [Tailscale Admin Console](https://login.tailscale.com/admin/settings/keys).
  - Paste the auth key into the `tailscale_authkey` workflow input.
  - Connect directly to `gha-ubuntu-xfce:3389` or the Tailscale IP shown in the step summary.
- **Using Ngrok**:
  - Provide your free [Ngrok Auth Token](https://dashboard.ngrok.com) in `ngrok_token`.
  - Connect to the `0.tcp.ngrok.io:xxxxx` address displayed in the summary.

---

## 🖥️ System Specs & Features

- **OS**: Ubuntu 24.04 LTS (Noble Numbat)
- **Desktop**: XFCE4 with `Arc-Dark` theme + `Papirus-Dark` icons
- **Apps**: Firefox, Thunar File Manager, XFCE Terminal, Mousepad, Htop
- **Compute**: 2 vCPUs, 7 GB RAM, ~20+ GB SSD free space
- **Network**: 1Gbps+ GitHub runner backbone
- **Max Duration**: Up to 5.8 hours per session

---

## 🪟 Windows Server RDP

To run a **Windows Server (Datacenter)** cloud desktop:

1. Go to **Actions** -> **Windows Server RDP**.
2. Click **Run workflow**:
   - Provide `rdp_password` (default: `Admin@12345`).
   - Provide `tailscale_authkey` (or have `TAILSCALE_AUTHKEY` saved in repository secrets).
3. Open **Microsoft Remote Desktop** on your Mac/Windows:
   - **PC Name**: `gha-windows-rdp:3389` (or the `100.x.y.z:3389` IP shown in Summary).
   - **Username**: `runneradmin`
   - **Password**: `Admin@12345`

---

## 🍎 macOS Remote Desktop (Apple Silicon)

To run a **real macOS Apple Silicon VM**:

1. Go to **Actions** -> **macOS Remote Desktop**.
2. Click **Run workflow**:
   - Provide `vnc_password` (default: `Admin@12345`).
   - Provide `tailscale_authkey` (or have `TAILSCALE_AUTHKEY` saved in repository secrets).
3. Connect natively from your Mac:
   - Press **`Cmd + Space`** -> search for **Screen Sharing**.
   - Enter `gha-macos-rdp` (or the `100.x.y.z:5900` IP from Summary).
   - **Username**: `runner`
   - **Password**: `Admin@12345`
   - Alternatively, open in Safari: `vnc://100.x.y.z:5900`

---

## 🛑 Stopping Any Session
To shut down any runner before the timer runs out, go to the active run in GitHub Actions and click **Cancel workflow**. Tailscale will automatically unregister the machine on exit.
