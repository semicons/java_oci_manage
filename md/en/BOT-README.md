# Telegram Bot Command Reference

[简体中文](../BOT-README.md)

---

## Table of Contents

- [1. Bot Command Menu](#1-bot-command-menu)
- [2. Oracle Keyboard Menu](#2-oracle-keyboard-menu)

---

## 1. Bot Command Menu

### Cloud Operations

| Command | Description |
|---------|-------------|
| `/oracle` | Open Oracle Cloud operation keyboard |
| `/azure` | Open Azure Cloud operation keyboard |
| `/solusvm` | SolusVM panel VPS management |
| `/domain` | Cloudflare domain management |

### Account Management

| Command | Description |
|---------|-------------|
| `/me` | View personal Lightning subscription info |
| `/raninfo` | Generate or reset random user credentials (save these for rebinding) |
| `/flash` | Compare standard vs Lightning privileges |
| `/migrate` | Transfer Lightning privileges to current account. Usage: `/migrate old_username old_password` |

### Payment & Activation

| Command | Description |
|---------|-------------|
| `/qrcode` | QR code payment for Lightning privileges (auto-activated after payment) |
| `/codeflash` | Activate with transaction order number. Usage: `/codeflash order_number` |
| `/getflash` | Activate with activation code. Usage: `/getflash code` |

### Configuration

| Command | Description |
|---------|-------------|
| `/oci` | Upload Oracle or Azure configuration to current client |
| `/pubkey` | Add SSH public key for instance boot |
| `/uploadapi` | Add new API configuration |
| `/oproxy` | Add HTTP proxy to a client profile |

### Others

| Command | Description |
|---------|-------------|
| `/command` | Execute shell command on current client |
| `/clearlock` | Clear lockout from too many password errors |
| `/qb` | Payment not received / advertising cooperation feedback |
| `/qs` | Lightning user support hotline |

> Admin-only commands should not be used by regular users.

---

## 2. Oracle Keyboard Menu

Open the operation keyboard via the `/oracle` command. Available functions:

### Instance Operations

| # | Feature | Description |
|---|---------|-------------|
| 1 | **Boot (ARM)** | Custom OS and CPU type boot. "aarch" = ARM type, delay in seconds. Requires secondary confirmation |
| 3 | **Boot Suspended** | Boot suspended instances directly without deleting disks |
| 5 | **Scale Up/Down** | Adjust CPU and memory configuration |
| 6 | **Instance Mgmt** | Delete, attach IPv4/IPv6, smart reserved IP attach, monitoring toggle, force restart, rename, reset OS |
| 17 | **Quick Boot** | Save boot configs; batch boot across multiple profiles/clients |

### IP & Networking

| # | Feature | Description |
|---|---------|-------------|
| 2 | **IP Management** | Change IP, quick Cloudflare domain binding, auto DNS update on IP change (pseudo-DDNS), delete domain, delete IP |
| 4 | **IPv6 Management** | IPv6 change operations |
| 11 | **Open Ports** | One-click open all ports and clear firewall rules (Oracle console security groups) |
| 16 | **Monitor (Auto IP)** | Set IP monitoring to trigger auto IP change + domain binding; supports proxy detection and IP range filtering |

### Disk Management

| # | Feature | Description |
|---|---------|-------------|
| 7 | **Disk Management** | Boot disk delete, resize (increase only), detach/attach, max VPU performance for IO boost |

### Account & Configuration

| # | Feature | Description |
|---|---------|-------------|
| 8 | **Cloud Account Mgmt** | Add admin with API, reset password, batch query emails, delete users |
| 13 | **Profile Management** | Switch / delete multiple configuration profiles |
| 14 | **Client Management** | Switch / delete multiple clients |
| 26 | **Clear All 2FA** | Reset two-step verification (API must have corresponding permissions) |
| 27 | **Disable Banned** | Check and comment out banned account configs (non-destructive) |
| 28 | **Delete Current API** | Permanently delete API key (⚠️ irreversible — may lose account access) |

### Monitoring & Notifications

| # | Feature | Description |
|---|---------|-------------|
| 9 | **Status Monitor Alert** | Periodic monitoring with Telegram notifications on anomalies |
| 10 | **Status Monitor Auto-Start** | Periodic monitoring with auto instance restart on anomalies |
| 29 | **Daily Report** | Scheduled push of cost and traffic usage |

### Queries

| # | Feature | Description |
|---|---------|-------------|
| 12 | **Workflow Errors** | Query last 3 Oracle workflow errors |
| 15 | **Health Check** | Batch check all profiles and clients |
| 18 | **Subscription Info** | Query free subscription date and amount |
| 19 | **3-Month Traffic** | Query traffic usage |
| 20 | **Query Quota** | Instance, network, storage quotas |
| 21 | **Running Tasks** | View all boot and upgrade tasks across clients |
| 22 | **Client Load** | View current client load |
| 25 | **3-Month Costs** | Paid account cost details (multi-region: query from main account) |
| 30 | **Batch Query Emails** | Query emails for all profiles |
| 34 | **Latest Logs** | View client's latest log output |

### System Operations

| # | Feature | Description |
|---|---------|-------------|
| 23 | **Occupy 25% Memory** | Smart memory fill to 25% |
| 24 | **Clear Cache & Memory** | Clear memory cache and 25% occupation |
| 31 | **Restart** | Restart current client |
| 32 | **Upgrade Client** | Detect and upgrade all clients (interrupts all operations during upgrade) |
| 33 | **Auto Expand Sub-regions** | Auto-find and add sub-domain subscriptions |
