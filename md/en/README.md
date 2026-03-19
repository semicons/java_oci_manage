# R-Bot ⭐

<p align="left">
  <a href="../../README.md"><img src="https://img.shields.io/badge/语言-简体中文-blue"/></a>
  <a href="https://t.me/apchyo"><img src="https://img.shields.io/static/v1?label=Group&message=Telegram&color=brightgreen"/></a>
  <a href="https://t.me/agentONE_R"><img src="https://img.shields.io/static/v1?label=Channel&message=Telegram&color=blueviolet"/></a>
  <a href="https://t.me/radiance_helper_bot"><img src="https://img.shields.io/static/v1?label=Bot&message=Telegram&color=red"/></a>
  <img src="https://img.shields.io/github/stars/semicons/java_oci_manage.svg?style=flat-square&label=Stars&logo=github"/>
</p>

## Overview

R-Bot is a **dual-architecture** multi-cloud infrastructure management system that drives a local client through a Telegram bot for quick management of Oracle Cloud (OCI), Azure, SolusVM, and more. The client also includes a built-in **Web SSH Terminal** and **Web Cloud Management Panel**, providing in-browser server operations and cloud resource management.

### Key Features

| Feature | Description |
|---------|-------------|
| **Dual-Architecture Security** | API private keys are stored only on your local client; the bot stores no sensitive data |
| **Telegram Bot Management** | 30+ cloud operations: boot instances, manage IPs, disks, monitoring, etc. |
| **Web SSH Terminal** | In-browser SSH with multi-tab, SFTP, and port forwarding |
| **Web Cloud Management** | Manage instances, networks, volumes, users, DNS, object storage from your browser |
| **Multi-Cloud Support** | Oracle Cloud, Azure, SolusVM, Cloudflare DNS |
| **GraalVM Native Compilation** | Sub-second startup, low memory footprint |

![Web SSH Terminal](../../screenshots/terminal.jpg)

---

## Quick Start

### 1. Follow the Channel and Bot

- [Telegram Channel](https://t.me/agentONE_R) — Update notifications
- [Telegram Bot](https://t.me/radiance_helper_bot) — Get credentials and control panel

### 2. One-Click Install

```bash
wget -O sh_client_bot.sh https://github.com/semicons/java_oci_manage/releases/latest/download/sh_client_bot.sh && chmod +x sh_client_bot.sh && bash sh_client_bot.sh
```

> Recommended: create a directory first — `mkdir rbot && cd rbot`

### 3. Configure

Use `/raninfo` in the bot to generate user credentials, fill `username` and `password` into the `client_config` file, and add your cloud API parameters.

Details → [Installation & Configuration](./install.md)

### 4. Start

```bash
bash sh_client_bot.sh
```

After startup, the Web SSH terminal is available at `https://YOUR_IP:9527` (HTTPS).

---

## Feature Overview

### Telegram Bot — Cloud Management

Operated through the Telegram bot, supporting Oracle Cloud and Azure.

- **Instance Management** — Boot, scale up/down, reset OS, terminate
- **IP Management** — Change IP, auto DNS update, IPv6
- **Disk Management** — Resize, performance tuning, detach/attach
- **Monitoring & Alerts** — Status monitoring, auto IP change, auto-restart
- **Account Management** — User management, API keys, 2FA reset, quota queries

Full list → [Implemented Features](./function.md) ｜ [Bot Commands](./BOT-README.md)

### Web SSH Terminal

Access through your browser — no client software required.

- **SSH Connections** — Password and private key auth, multi-tab
- **SFTP File Manager** — Browse, upload, download, create directories
- **Port Forwarding** — Local and remote forwarding
- **Batch Commands** — Send commands to multiple sessions simultaneously
- **Session Management** — Save connection profiles, centralized key management
- **SSL Certificates** — Built-in ACME auto-provisioning (Let's Encrypt)
- **OCI Object Storage** — Manage Buckets and objects in-browser

Details → [Web SSH Terminal Guide](./webssh.md)

### Web Cloud Management Panel

Manage multi-cloud resources directly from your browser — fully aligned with the Telegram bot's capabilities.

- **Instance Management** — Start, stop, reboot, terminate, reset OS, scale up/down
- **Network Management** — Change IP, attach IPv4/IPv6, reserved IP management
- **Volume Management** — Resize, VPU performance tuning, detach/delete
- **User Management** — Create users, reset passwords, update email, clear 2FA
- **Statistics Overview** — Cost, traffic, subscription info, quota queries
- **DNS Management** — Cloudflare domain record CRUD operations
- **Object Storage** — OCI Object Storage bucket and file management
- **Azure Management** — VM create/delete/restart, change IP, resource usage
- **SolusVM Management** — VPS boot/shutdown/reboot, status dashboard

Details → [Web Cloud Management Guide](./cloud.md)

![Web Cloud Management](../../screenshots/cloud-dashboard.jpg)

---

## Documentation

| Document | Description |
|----------|-------------|
| [Installation & Configuration](./install.md) | Install script, config parameters, startup commands |
| [Implemented Features](./function.md) | Full feature list (Bot + Web SSH + Cloud Management) |
| [Bot Commands](./BOT-README.md) | Telegram bot commands and keyboard menus |
| [Web SSH Terminal](./webssh.md) | Web SSH terminal feature guide |
| [Web Cloud Management](./cloud.md) | Web cloud management panel guide |
| [Oracle Cloud API Setup](./oracle.md) | How to get and upload OCI API parameters |
| [Azure API Setup](./azure.md) | How to get and upload Azure API parameters |
| [FAQ](https://t.me/agentONE_R/41) | Pinned FAQ in Telegram channel |

---

## Common Commands

```bash
# Start / Restart (daemon mode)
bash sh_client_bot.sh

# Start with custom port
bash sh_client_bot.sh 8888

# View status
bash sh_client_bot.sh status

# View logs (Ctrl+C to exit)
bash sh_client_bot.sh log

# Stop
bash sh_client_bot.sh stop

# Restart
bash sh_client_bot.sh restart

# Upgrade
bash sh_client_bot.sh upgrade

# Uninstall
bash sh_client_bot.sh uninstall
```

---

## Architecture

```
User → Telegram → R-Bot Server → HTTP/WS → Local Client → Cloud SDK
User → Browser → Local Client (Web UI) → Cloud SDK
```

- **R-Bot Server** — Receives Telegram commands, routes to client
- **Local Client** — Wraps cloud platform SDK calls, provides Web SSH + Cloud Management UI
- **API Keys** — Stored only on the local client; server never touches them

---

## Supported Platforms

| Architecture | Package |
|-------------|---------|
| Linux x86_64 (AVX2) | `gz_client_bot_x86.tar.gz` |
| Linux x86_64 (compatible) | `gz_client_bot_x86_compatible.tar.gz` |
| Linux ARM64 | `gz_client_bot_aarch.tar.gz` |
| macOS ARM64 (Apple Silicon) | `gz_client_bot_mac_aarch.tar.gz` |

> The startup script auto-detects architecture and downloads the correct version.

---

## Disclaimer

> This system uses a dual-architecture design. API private keys are stored on your local client server. The bot drives your client operations, and you can shut down the service at any time. If you have concerns, please do not use this software.
>
> <details>
> <summary>Full Disclaimer</summary>
>
> Any scripts involved in the projects published in this repository are for testing and research purposes only. Commercial use is prohibited. We cannot guarantee their legality, accuracy, completeness, or validity. Please judge according to your situation.
>
> All users must comply with applicable laws and regulations when using any part of this project. Users bear all consequences of improper use. We are not responsible for any script issues, including but not limited to any losses or damages caused by script errors.
>
> If any entity or individual believes this project may infringe upon their rights, they should promptly notify us and provide identification and proof of ownership. We will remove relevant files upon receipt of certified documentation.
>
> Anyone who views or directly or indirectly uses any scripts from this project should carefully read this disclaimer. We reserve the right to modify or supplement this disclaimer at any time. By using or copying any related scripts or rules of this project, you are deemed to have accepted this disclaimer.
>
> You must completely delete the above content from your computer or phone within 24 hours of downloading. By using or copying any scripts made by us in this repository, you are deemed to have accepted this disclaimer. Please read carefully.
> </details>
