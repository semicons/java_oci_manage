# Implemented Features

[简体中文](../function.md)

---

## Telegram Bot — Oracle Cloud (OCI)

- [x] Boot instances (AMD / ARM / Intel, custom configuration)
- [x] IP management (query, change, auto DNS update)
- [x] Boot suspended instances
- [x] IPv6 management (attach, change)
- [x] Scale up / down instances (CPU, memory)
- [x] Instance management (delete, rename, force restart, reset OS, monitoring toggle)
- [x] Disk management (resize, performance tuning, detach/attach, delete)
- [x] Cloud account management (add admin, reset password, query emails, delete users)
- [x] Instance status monitoring + alert notifications
- [x] Instance status monitoring + auto-restart
- [x] One-click open all security group ports
- [x] Oracle workflow error query
- [x] Multi-profile / multi-client management
- [x] One-click account health check (batch detect all account status)
- [x] Auto IP change monitoring (with DNS binding, IP range filtering)
- [x] Quick boot (save configs, batch multi-profile boot)
- [x] Oracle subscription info query
- [x] Last 3 months traffic query
- [x] Quota query (instances, network, storage)
- [x] Running task viewer
- [x] Client load viewer
- [x] Smart memory occupation (fill to 25%)
- [x] Last 3 months cost query
- [x] Clear all 2FA devices
- [x] One-click disable banned accounts
- [x] Delete API key
- [x] Daily cost and traffic reports
- [x] Batch email query
- [x] Cloudflare domain quick actions
- [x] Local mode without public IP

## Telegram Bot — Azure

- [x] Custom boot
- [x] Change IP
- [x] Delete instance
- [x] Query quota usage
- [x] Delete all resources

## Telegram Bot — SolusVM

- [x] SolusVM panel VPS management

---

## Web SSH Terminal

- [x] In-browser SSH connections (password / private key auth)
- [x] Multi-tab parallel terminals
- [x] SFTP file management (browse, upload, download, create directories)
- [x] SSH port forwarding (local / remote)
- [x] Batch commands (send to multiple sessions simultaneously)
- [x] Session profile save & management
- [x] Centralized SSH key management (encrypted storage, smart matching)
- [x] Host fingerprint verification (SHA256)
- [x] Auto host specs detection (OS, CPU, memory, disk)
- [x] OCI Object Storage management (bucket browsing, file CRUD)
- [x] Resource monitor panel (top bar displaying real-time CPU / memory / disk / network metrics)
- [x] ACME auto SSL certificates (Let's Encrypt)
- [x] Telegram verification code login + anti-brute-force
- [x] Chinese/English interface switching
- [x] Responsive layout (mobile-friendly)
- [x] HTTPS (TLSv1.3) + HTTP/2

---

## Web Cloud Management Panel

### Oracle Cloud

- [x] Instance management (create, quick boot, start, stop, reboot, terminate, reset OS, scale, rename, repair)
- [x] Network management (change IP, attach IPv4/IPv6, reserved IP, delete IP)
- [x] Volume management (resize, VPU performance, detach, delete, batch VPU)
- [x] User management (create, delete, reset password, update email, clear 2FA, rename tenant)
- [x] Statistics overview (cost, traffic, subscription info, quota)
- [x] Profile management (list, switch, delete)
- [x] Object Storage management (bucket browsing, file upload/download/delete)
- [x] Instance monitoring alerts / auto-start / daily report / health check
- [x] Email Delivery (one-click email domain setup, DKIM/DNS auto-config, SMTP credential management, test send)

### Cloudflare DNS

- [x] Zone listing, DNS record CRUD operations

### Azure

- [x] VM management (list, create, delete, restart, change IP)
- [x] Resource usage query

### SolusVM

- [x] VPS management (node list, dashboard, boot/shutdown/reboot)

---

## In Development

- [ ] More cloud platform management features in progress
