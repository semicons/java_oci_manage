# Web Cloud Management Panel Guide

[简体中文](../cloud.md)

The R-Bot client includes a full-featured Web cloud management panel. Manage Oracle Cloud, AWS, Azure, SolusVM, and Cloudflare DNS resources directly from your browser — fully aligned with the Telegram bot's capabilities.

---

## Access

After starting the client, visit:

```
https://YOUR_IP:9527
```

Log in and access the cloud management workbench via the view switcher from the host dashboard.

> First-time users need to configure cloud platform Profiles in the top bar "Settings" or via the `client_config` file.

---

## Overview Dashboard

The home page displays overview information for the current Profile:

| Card | Content |
|------|---------|
| **Cost** | Last 3 months spending details |
| **Traffic** | Last 3 months traffic usage |
| **Subscription** | Subscription type, payment, validity |
| **Quota** | Instance, network, storage quota usage |

Switch between Profiles to view different account information.

---

## Oracle Cloud Management

### Instance Management

| Action | Description |
|--------|-------------|
| View Instance List | Display all instances and status |
| Create Instance | Create a new instance with custom specs, image, and network |
| Force ARM Boot | Improve ARM instance creation success rate for trial accounts (briefly uses paid features, use at your own risk) |
| Quick Boot | Quickly create an instance from saved configurations |
| Start / Stop / Reboot | Basic instance operations |
| Terminate | Delete instance (optionally preserve boot volume) |
| Reset Image | Reinstall to initial OS image |
| Scale Up/Down | Adjust CPU and memory specs |
| Rename | Change instance display name |
| Repair | Attempt to repair abnormal instance |

![Create Instance](../screenshots/cloud-create.jpg)

### Network / IP Management

| Action | Description |
|--------|-------------|
| View VNICs | Display NICs, private IPs, public IPs |
| Change IPv4 | Change public IPv4 address |
| Change IPv6 | Change IPv6 address |
| Delete IP | Remove public IP or IPv6 |
| Attach IPv4 | Add additional IPv4 to instance |
| Attach IPv6 | Create new IPv6 address |
| Attach Reserved IP | Attach a reserved public IP |

### Volume Management

| Action | Description |
|--------|-------------|
| View Volumes | Display all block storage volumes |
| Resize | Increase volume size (cannot shrink) |
| Adjust VPU | Modify performance units for IO boost |
| Batch VPU | Max out VPU for all volumes at once |
| Detach | Detach volume from instance |
| Delete | Permanently delete block storage volume |

### User Management

| Action | Description |
|--------|-------------|
| List Users | Display all users in the tenancy |
| Create User | Add a new admin user |
| Update Email | Change user email address |
| Reset Password | Reset user login password |
| Clear 2FA | Remove bound two-factor authentication |
| Change Tenant Name | Modify tenancy display name |
| Delete User | Remove specified user |

### Object Storage (OSS)

| Action | Description |
|--------|-------------|
| Browse Buckets | List all storage buckets |
| Browse Objects | Prefix filtering and paginated browsing |
| Upload Files | Streaming upload with path traversal prevention |
| Download Files | Streaming download |
| Delete Objects | Delete individual files |
| Create Folders | Create directory structures |

### Profile Management

| Action | Description |
|--------|-------------|
| List Profiles | Display all configured OCI Profiles |
| Switch Profile | Switch to a different cloud account |
| Delete Profile | Remove unwanted Profiles |

### Email Delivery

| Action | Description |
|--------|-------------|
| One-Click Setup | Enter domain and sender address to automatically create email domain, DKIM signing, DNS records, sender registration, and SMTP credentials |
| DNS Mode | Supports Cloudflare auto-config and manual mode; manual mode pauses to display DNS records for user confirmation |
| Setup Progress | Async execution with real-time progress bar, resumable after leaving the page |
| Domain Management | View email domain list, DKIM verification status, and lifecycle state |
| DKIM Info | View DKIM CNAME record details for manual DNS configuration reference |
| DKIM Repair | Auto-reconfigure DNS CNAME records via Cloudflare when DKIM verification fails (async with progress tracking) |
| Sender Management | View senders under a specific domain and their status |
| Add Sender | Add a new sender address to an existing email domain |
| SMTP Config | View SMTP connection info (server/port/username) |
| Regenerate Credentials | Regenerate SMTP password (shown once, save it securely) |
| Test Send | Send test email via OCI HTTP API with custom recipient/subject/body |
| Delete Domain | Cascade delete email domain with associated DKIM and sender resources |

### Serial Console

Connect to an OCI instance's serial console via Console Connection — useful for emergency maintenance when SSH is unavailable.

| Action | Description |
|--------|-------------|
| Connect Console | Auto-generate temporary RSA key pair and establish SSH-over-SSH tunnel |
| WebSocket Terminal | Real-time serial terminal interaction in browser |
| Netboot.xyz Automation | Auto-detect UEFI/GRUB menus and boot into Netboot.xyz rescue system |
| Connection Management | Auto-reuse existing connections, 30-minute key TTL, scheduled cleanup of expired connections |
| User Confirmation | Semi-automatic confirmation workflow before dangerous operations |

---

## AWS Management

### EC2 Instance Management

| Action | Description |
|--------|-------------|
| View Instance List | Display all EC2 instances with real-time status |
| Create Instance | Select AMI image, instance type, SSH key; async creation with progress tracking |
| Start / Stop / Reboot | Basic instance power operations |
| Terminate | Permanently delete EC2 instance |

### Network Management

| Action | Description |
|--------|-------------|
| VPC Management | View and manage VPC resources |
| Security Groups | Manage security group configurations |

### Statistics & Monitoring

| Action | Description |
|--------|-------------|
| Cost Statistics | AWS Cost Explorer integration for spending details |
| Usage Monitoring | CloudWatch metrics queries |
| Quota Query | View resource quota usage |

---

## Cloudflare DNS Management

| Action | Description |
|--------|-------------|
| List Zones | Display all Cloudflare-managed domains |
| View Records | View all DNS records for a domain |
| Add Record | Create A/AAAA/CNAME and other DNS records |
| Edit Record | Modify existing DNS records |
| Delete Record | Remove specified DNS record |

---

## Azure Management

| Action | Description |
|--------|-------------|
| List VMs | Display all virtual machines and status |
| Create VM | Create a new virtual machine |
| Delete VM | Delete a virtual machine |
| Restart VM | Restart a virtual machine |
| Change IP | Change public IP address |
| Resource Usage | View quota usage |

---

## SolusVM Management

| Action | Description |
|--------|-------------|
| List Nodes | List all VPS nodes |
| Node Dashboard | View VPS status details |
| Boot / Shutdown / Reboot | VPS power operations |

---

## Settings

### Instance Monitoring

| Feature | Description |
|---------|-------------|
| Monitor Alerts | Periodic instance status monitoring with Telegram notifications |
| Auto-Start | Auto-start instances when anomalies detected |
| Daily Report | Scheduled push of cost and traffic reports |
| Health Check | Batch check all Profile account status |

### ACME Certificates

Configure Let's Encrypt auto-certificates in the Settings page. See [Web SSH Guide — SSL Certificates](./webssh.md#ssl-certificate-configuration) for details.

### Cloud Platform Configuration

Upload and manage cloud platform API configurations directly from the web interface — no need to manually edit the `client_config` file.

| Feature | Description |
|---------|-------------|
| OCI Config Upload | Paste API config text + upload PEM key file, key_file path auto-configured |
| AWS Config Upload | Paste Access Key ID / Secret Access Key configuration |
| Azure Config Upload | Paste appId/password/tenant configuration |
| SolusVM Config Upload | Paste API URL and key configuration |
| Merge Mode | Duplicate Profile names are skipped with a warning, new Profiles are appended |
| Cloudflare Config | Edit Cloudflare email and API Key online |
| Network Config | Edit local address, URL name, and startup mode online |
| Hot Reload | Manually refresh in-memory configuration without restarting the client |

---

## Themes

The web interface supports 8 themes, each with both light and dark modes:

| Theme | Style |
|-------|-------|
| Classic | Default blue, clean and professional |
| Sakura | Pink tones, ACG / anime style |
| Cyber | Neon cyan-blue, techy |
| Ink | Golden antique, Chinese traditional |
| Aurora | Teal-purple gradient, northern lights |
| Stellar | Deep purple tones, starry sky |
| Abyss | Deep ocean blue-green, bioluminescent |
| Sunset | Warm orange-coral, cozy |

Switch themes using the selector in the top bar. Toggle the light/dark mode button to switch between light and dark modes.
