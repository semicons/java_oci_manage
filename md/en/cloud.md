# Web Cloud Management Panel Guide

[简体中文](../cloud.md)

The R-Bot client includes a full-featured Web cloud management panel. Manage Oracle Cloud, Azure, SolusVM, and Cloudflare DNS resources directly from your browser — fully aligned with the Telegram bot's capabilities.

---

## Access

After starting the client, visit:

```
https://YOUR_IP:9527
```

Log in and navigate to the cloud management modules from the sidebar.

> First-time users need to configure cloud platform Profiles in "Settings" or via the `client_config` file.

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
| Start / Stop / Reboot | Basic instance operations |
| Terminate | Delete instance (optionally preserve boot volume) |
| Reset Image | Reinstall to initial OS image |
| Scale Up/Down | Adjust CPU and memory specs |
| Rename | Change instance display name |
| Repair | Attempt to repair abnormal instance |

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

---

## Themes

The web interface supports multiple theme options:

| Theme | Description |
|-------|-------------|
| Classic | Default dark theme |
| Other Themes | Sakura, Starry Sky, Abyss, etc. |

Switch themes using the selector in the top-right corner.
