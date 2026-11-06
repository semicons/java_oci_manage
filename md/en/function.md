# Implemented Features

[简体中文](../function.md)

---

## Telegram Bot — Oracle Cloud (OCI)

- [x] Launch instances (AMD / ARM / Intel, custom specs)
- [x] IP management (look up, change, update domain records while changing)
- [x] Start suspended instances directly (no need to delete the disk and rebuild)
- [x] IPv6 management (attach, change)
- [x] Resize (CPU, memory)
- [x] Instance management (terminate, rename, force reboot, reinstall, monitoring toggle)
- [x] Disk management (grow, faster IO, detach / attach, delete)
- [x] Cloud account management (add admins, reset passwords, look up emails, delete users)
- [x] Instance monitoring + alerts
- [x] Instance monitoring + auto-restart
- [x] Open all security list ports in one click
- [x] Oracle workflow error lookup
- [x] Multiple accounts / multiple clients
- [x] Health check across every account
- [x] Auto IP change when an IP stops responding (with domain binding and IP range filter)
- [x] Quick launch (save configs, launch across several accounts)
- [x] Launch alerts show account type (upgraded / regular)
- [x] Subscription info
- [x] Traffic over the last 3 months
- [x] Quota lookup (instances, network, storage)
- [x] Running tasks
- [x] Client load
- [x] Top up memory usage to 25%
- [x] Spending over the last 3 months
- [x] Clear all two-factor devices
- [x] Disable banned accounts in one go
- [x] Delete an API key
- [x] Daily spending and traffic report
- [x] Look up emails in bulk
- [x] Cloudflare domain shortcuts
- [x] Works without a public IP (local mode)

## Telegram Bot — AWS

- [x] EC2 instances (list, start, stop, reboot, terminate)
- [x] Create EC2 instances (image, type, key)
- [x] Lightsail instances (list, start, stop, reboot, delete, traffic)
- [x] Change IP
- [x] Costs
- [x] Quotas

## Telegram Bot — GCP

- [x] Instances (list, start, stop, reboot, delete)
- [x] Create instances (zone, machine type, OS, disk size, SSH key)
- [x] Change IP
- [x] Overview (instance count, zone spread, free-tier usage)
- [x] Traffic over the last 3 months

## Telegram Bot — Azure

- [x] Custom launch
- [x] Change IP
- [x] Delete instances
- [x] Quotas
- [x] Delete all resources

## Telegram Bot — DigitalOcean

- [x] Droplets (list, details, power on, power off, reboot, destroy)
- [x] Switch accounts
- [x] Monthly traffic per instance

## Telegram Bot — VirtFusion

- [x] Instances by vendor
- [x] Instance details (state, CPU, memory, disk, IP, traffic, creation time)
- [x] Power on / off / reboot / force off
- [x] Reset system password

## Telegram Bot — SolusVM

- [x] VPS management

---

## Web SSH Terminal

- [x] SSH in the browser (password / private key, SOCKS5 proxy)
- [x] Tabs
- [x] SFTP file manager (browse, upload, download, delete, new folder)
- [x] Edit server files online (syntax highlighting)
- [x] Transfer manager (progress, speed, cancel, recent history)
- [x] File transfer to devices without SFTP, such as OpenWrt
- [x] Port forwarding (local / remote)
- [x] Auto-reconnect
- [x] Batch commands (one command to many hosts, keep going from the results page)
- [x] Terminal toolbar (favorites, search, common tools)
- [x] Multi-line paste protection (pasted lines wait for Enter)
- [x] Terminal image paste (paste screenshots to Claude Code and Codex in the web terminal)
- [x] Host tags and filtering
- [x] Split screen (two panes, one-click clone, kept across refresh)
- [x] Session suspend (close the page without disconnecting, reattach later)
- [x] Persistent shell (commands keep running after the browser closes)
- [x] Resource alerts (CPU / memory / disk thresholds over Telegram)
- [x] Multi-cloud overview (instance state across every cloud on one page)
- [x] Saved connections
- [x] Central SSH key store (saved keys tried automatically)
- [x] Server OS and specs detected automatically
- [x] Live CPU / memory / disk / network usage
- [x] OCI Object Storage
- [x] Let's Encrypt certificates, issued and renewed automatically
- [x] Cloud host sync (import existing machines from every cloud)
- [x] Upload and edit cloud configs in the browser, effective on save
- [x] MCP access (let Claude Code, Codex, and Cursor work on the servers you authorize, through the panel; tokens can be renewed and their hosts changed)
- [x] Upgrade, restart, and read logs of the client from the browser
- [x] Telegram code login
- [x] Chinese and English interface
- [x] Stays on the same page after refresh
- [x] Support chat (images supported)
- [x] Works on phones

---

## Web Cloud Management

### Oracle Cloud

- [x] Instances (create, quick boot, force ARM, start, stop, reboot, terminate, reinstall, resize, rename, repair)
- [x] Quick config (AMD Micro 1C/1G, ARM A1 2C/12G in one click)
- [x] Launch from an existing boot volume
- [x] Launch result shown on the page
- [x] Networking (change IP, attach IPv4 / IPv6, reserved IPs, delete IP)
- [x] Disks (grow, faster IO, detach, attach, delete)
- [x] Put a detached boot volume back on its instance
- [x] A1 audit / downscale (find accounts over the ARM free allowance and bring them back, never deleting instances on its own)
- [x] Users (create, delete, reset password, change email, clear two-factor, rename tenancy, view password policy)
- [x] Overview (cost, traffic, subscription, quota)
- [x] Accounts (switch, delete, copy to a new region)
- [x] Per-account API outbound proxy
- [x] Object Storage
- [x] Instance alerts / auto-start / daily report / health check
- [x] Serial console (rescue instances you cannot SSH into, including Netboot.xyz rescue)
- [x] Email Delivery (sending domain and SMTP account set up in one click, test send)

### AWS

- [x] EC2 instances (list, create, start, stop, reboot, terminate, add IPv6)
- [x] EC2 firewall / security groups (attach, detach, create, delete, edit rules, one-click presets)
- [x] Lightsail instances (create, list, start, stop, reboot, delete, monthly traffic)
- [x] Lightsail network / IP (static IP, change IP, firewall ports, IPv6 on / off)
- [x] VPC
- [x] Costs
- [x] Quotas

### GCP

- [x] Instances (list, create, start, stop, reboot, delete, change IP)
- [x] Overview (instance count, zone spread, free-tier usage)
- [x] Traffic over the last 3 months

### Cloudflare DNS

- [x] Domain list, DNS record management
- [x] API token or Global API Key

### DigitalOcean

- [x] Droplets (list, create, power on, power off, reboot)
- [x] Reserved IPs (assign, attach, detach, release)
- [x] Traffic
- [x] Billing overview

### Azure

- [x] VMs (list, create, delete, restart, change IP)
- [x] Quotas

### SolusVM

- [x] VPS (list, status, power, reboot)

### VirtFusion

- [x] Instances grouped by vendor
- [x] Current-period traffic
- [x] One-click SSH
- [x] Power on / off / reboot / force off
- [x] Rename
- [x] Reset system password

### Cloud & Domain Monitoring

- [x] Traffic guard (per-account traffic limit; notify or shut down automatically)
- [x] Uptime guard (notify or restart when an instance stops unexpectedly)
- [x] Domain and SSL certificate expiry reminders (30 / 14 / 7 / 1 days before, over Telegram)
- [x] One-click import of domains from Cloudflare

### General

- [x] One-click SSH from any cloud's instance card

---

## In Progress

- [ ] More cloud operations on the way
