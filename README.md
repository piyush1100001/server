# ⚡ 60 FPS Cloud Remote Desktop Suite on GitHub Actions (Sunshine + Moonlight + Tailscale)

This repository provides an automated, high-performance **60 FPS cloud desktop suite** running on GitHub Actions free hosted runners.

### 🎮 Powered by:
- **🌙 Moonlight + ☀️ Sunshine**: Ultra-low-latency (<10ms) 60 FPS video & high-fidelity audio streaming.
- **🛡️ Tailscale**: Direct WireGuard encrypted peer-to-peer connection with zero open port exposure.
- **🌐 Cloudflare Quick Tunnels**: Instant 1-click web browser access without installing any client software.

---

## 🖥️ Supported Operating Systems

| OS / Desktop | 60 FPS Moonlight / Sunshine | RustDesk (Web + App) | Native RDP / VNC | 1-Click Web Access |
| :--- | :--- | :--- | :--- | :--- |
| **🍎 macOS Apple Silicon** | ❌ | ✅ **Yes (9-digit ID)** | ❌ (Apple Lock) | ✅ **[web.rustdesk.com](https://web.rustdesk.com)** |
| **🐧 Ubuntu 24.04 LTS (XFCE)** | ✅ **Yes (Port 47989/47990)** | ❌ | ✅ XRDP (`:3389`) | ✅ noVNC (`trycloudflare.com`) |
| **🪟 Windows Server 2025** | ✅ **Yes (Port 47989/47990)** | ❌ | ✅ Microsoft RDP (`:3389`) | ❌ N/A |

---

## 🍎 How to Access macOS with RustDesk (Web & App):
1. Launch **macOS Remote Desktop** in **Actions** (provide your password).
2. Open the **Summary tab** to get your **RustDesk Device ID** (e.g. `123 456 789`).
3. **Web Browser Access (Zero Client Install):** Open **[web.rustdesk.com](https://web.rustdesk.com)** in Safari/Chrome, enter the Device ID and password, and stream macOS directly in your browser!
4. **Native App:** Or download the free **[RustDesk](https://rustdesk.com)** client for Mac, Windows, iOS, or Android.

---

## 🌙 How to Stream at 60 FPS with Moonlight & Sunshine:

### Step 1: Install Moonlight on your Mac/Windows/Phone
Download the free client app: **[Moonlight Stream](https://moonlight-stream.org/)** (available for Mac, Windows, iOS, Android, Linux).

### Step 2: Launch the Workflow on GitHub
1. Go to **Actions** -> Select **Ubuntu 24.04 XFCE Fast Remote Desktop** or **Windows Server RDP**.
2. Click **Run workflow** (provide your password & Tailscale key).
3. Once running, open the **Summary** tab to get your Tailscale IP (e.g. `100.x.y.z`).

### Step 3: Pair Moonlight (Takes 5 seconds, only needed once per runner)
1. In the **Moonlight** app, click **Add Host (+)** and enter your Tailscale IP (`100.x.y.z`).
2. Moonlight will display a **4-digit PIN** on your screen (e.g. `1234`).
3. Open the Sunshine Dashboard in Safari/Chrome: `https://<tailscale-ip>:47990`
   - Log in with Username: `admin` / Password: `Admin@12345` (or your configured password).
4. Click on the **PIN** tab -> enter the 4-digit PIN -> Click **Send**.
5. Click **Desktop** in Moonlight!

🎉 **You are now streaming your cloud desktop at true 60 FPS with low latency and crystal-clear audio!**

---

## 🛑 Stopping a Session
Click **Cancel workflow** in GitHub Actions. Tailscale will automatically log out and clean up the runner from your devices.
