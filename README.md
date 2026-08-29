# Ubuntu 24.04 LTS KDE Remote Desktop on GitHub Actions

This repository provides an automated GitHub Actions workflow to spin up an **Ubuntu 24.04 LTS runner with a full KDE Plasma Desktop** environment accessible from **Mac, Windows, Linux, and Mobile** using 100% free tools (Cloudflare Quick Tunnels, noVNC, and XRDP).

---

## ⚡ Quick Start Guide

### 1. Launch the Desktop Workflow
1. Go to your repository on GitHub.
2. Click on the **Actions** tab.
3. Select **Ubuntu 24.04 KDE Remote Desktop** from the left sidebar.
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
4. Enter your password and click **Connect**.
5. You now have full graphical access to KDE Plasma with clipboard and file manager support.

### Option 2: Native Microsoft Remote Desktop (XRDP)
If you prefer the native **Microsoft Remote Desktop** app on Windows or Mac:
- **Using Tailscale (Recommended for fast, direct, encrypted connection)**:
  - Generate an auth key from [Tailscale Admin Console](https://login.tailscale.com/admin/settings/keys).
  - Paste the auth key into the `tailscale_authkey` workflow input.
  - Connect directly to `gha-ubuntu-kde:3389` or the Tailscale IP shown in the step summary.
- **Using Ngrok**:
  - Provide your free [Ngrok Auth Token](https://dashboard.ngrok.com) in `ngrok_token`.
  - Connect to the `0.tcp.ngrok.io:xxxxx` address displayed in the summary.

---

## 🖥️ System Specs & Features

- **OS**: Ubuntu 24.04 LTS (Noble Numbat)
- **Desktop**: KDE Plasma Desktop (`plasma-workspace`, `dolphin`, `konsole`, `kate`)
- **Web Browser**: Firefox pre-installed
- **Compute**: 2 vCPUs, 7 GB RAM, ~20+ GB SSD free space
- **Network**: High speed 1Gbps+ GitHub runner backbone
- **Max Duration**: Up to 5.8 hours per session (re-runnable anytime)

---

## 🛑 Stopping the Session
To shut down the runner before the timer runs out, go to the active run in GitHub Actions and click **Cancel workflow**.
