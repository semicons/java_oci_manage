# Web SSH Terminal Guide

[简体中文](../webssh.md)

The R-Bot client includes a full-featured Web SSH terminal. Connect to and manage remote servers directly from your browser — no client software required.

---

## Access

After starting the client, visit:

```
https://YOUR_IP:9527
```

> Uses HTTPS + TLSv1.3 by default. On first visit, the browser will warn about the self-signed certificate — you can trust it manually or configure ACME auto-certificates.

---

## Page Layout

After login, the main interface uses a **four-view switching** layout:

```
┌─────────────────────────────────────────────────────┐
│ Top Bar: Brand | Language | Theme | Lightning |      │
│          Settings | Logout                           │
├─────────────────────────────────────────────────────┤
│                                                     │
│  Main Content (View Switching)   Config Drawer      │
│  · Host Dashboard                (slides from right)│
│  · Terminal Workspace                               │
│  · Cloud Management                                 │
│  · Lightning Benefits                               │
│                                                     │
└─────────────────────────────────────────────────────┘
```

| Area | Description |
|------|-------------|
| **Top Bar** | Brand logo "R·Cloud·SSH", language selector, theme picker (8 themes), Lightning entry, settings menu (SSL Certificates / Config Files), light/dark mode toggle, logout |
| **Host Dashboard** | Default view after login — displays all saved host sessions as a card grid with search, cloud host sync, add session, and batch selection |
| **Terminal Workspace** | Auto-switches when connecting to a host — includes tab bar, terminal panes, and SFTP panel (drag-resizable height) |
| **Cloud Management** | Multi-cloud resource management workbench — see [Cloud Management Guide](./cloud.md) |
| **Config Drawer** | Right-sliding panel for connection details, authentication, and port forwarding configuration |

---

## Login Authentication

Two login methods are supported:

### Password Login

Log in directly using the `username` and `password` configured in `client_config`.

### Telegram Verification Code

1. Click "Send Verification Code"
2. The bot sends an 8-digit code via Telegram
3. Enter the code within 60 seconds to log in

> Anti-abuse protection: After 3 consecutive requests within 10 minutes, a CAPTCHA (arithmetic question) is triggered to prevent brute-force attacks.

![Login Page](../../screenshots/login.jpg)

---

## SSH Connections

### New Connection

1. Click "Add Session" in the host dashboard — the config drawer slides in from the right
2. Fill in connection details:
   - **Session Name** — Custom name (optional)
   - **Host** — IP address or domain name
   - **Port** — Default 22
   - **Username** — SSH login user
   - **Auth Method** — Password or private key
3. Click "Connect" to auto-switch to the terminal workspace

### Authentication Methods

| Method | Description |
|--------|-------------|
| **Password** | Enter SSH password |
| **Private Key** | Paste key content or select a saved key; supports passphrase |

### Host Fingerprint Verification

On first connection, the SHA256 host fingerprint is displayed for confirmation and saved. If the fingerprint changes on subsequent connections (possibly due to server reinstallation or a security risk), a warning is shown.

### Quick Connect

In the host dashboard, click the "Quick Connect" button on a saved host card to connect directly without re-entering details. Click the "Load" button to open the config drawer for editing connection parameters.

### Auto-Reconnect

When an SSH connection is interrupted (e.g., server reboot or network fluctuation), the terminal automatically attempts to reconnect using an exponential backoff strategy — no manual action needed to restore the session.

### Multi-Tab

Multiple SSH connections can be open simultaneously, each in its own tab, freely switchable. The tab bar also integrates system resource monitoring metrics (CPU / Memory / Disk / Network).

![Terminal Interface](../../screenshots/terminal.jpg)

---

## SFTP File Manager

After connecting via SSH, click the "SFTP" button in the tab bar to open the file management panel. The SFTP panel appears below the terminal and supports **drag-resizing** the divider to adjust the height ratio between terminal and SFTP.

### Features

| Action | Description |
|--------|-------------|
| **Browse Directories** | Click folders to enter; breadcrumb navigation for quick jumping |
| **Upload Files** | Chunked upload with progress display |
| **Download Files** | Streaming transfer with 512KB chunks + sliding window acknowledgment |
| **Online Edit** | syntax highlighting — edit server files directly in the browser |
| **Delete Files/Folders** | Inline confirmation, supports recursive directory deletion |
| **Create Directory** | Create new folders in the current path |

<!-- Screenshot placeholder: SFTP file management panel -->
<!-- ![SFTP Panel](../../screenshots/sftp.png) -->

---

## Port Forwarding

Configure SSH port forwarding in the config drawer (while connected).

### Local Forward

Map a remote service to a local port (e.g., access a remote database):

| Parameter | Example |
|-----------|---------|
| Bind Address | `127.0.0.1` |
| Bind Port | `3306` |
| Target Address | `127.0.0.1` |
| Target Port | `3306` |

### Remote Forward

Expose a local service to a port on the remote server.

<!-- Screenshot placeholder: Port forwarding configuration -->
<!-- ![Port Forwarding](../../screenshots/port-forward.png) -->

---

## Batch Commands

Send the same command to multiple hosts simultaneously — ideal for batch operations.

1. In the host dashboard, check the target host cards (multi-select supported)
2. A batch toolbar automatically appears at the bottom showing the selected count
3. Enter the command in the input field and click execute
4. Enter the result workbench — results are displayed in real-time as grid cards showing each host's execution status and output
5. Continue executing new commands directly in the result workbench without re-selecting hosts

---

## Session Management

### Host Dashboard

The default view after login displays all saved sessions as a **responsive card grid**. Each card shows:

- Session name and description
- Host specs (OS, CPU, memory, disk — auto-detected after connection)
- IP address(es) with one-click copy
- Last modified timestamp
- Action buttons: Quick Connect, Load Config, Delete

The dashboard header provides a search box (filter by name / IP) and an "Add Session" button.

### Save Sessions

After a successful connection, save the current configuration as a session from the config drawer for one-click reconnection from the host dashboard. Saved information includes:

- Session name, description
- Host, port, username
- Auth method and credentials (encrypted storage)

### SSH Key Management

Centralized management of all SSH private keys:

- Add / delete keys
- Concurrent smart matching of saved keys when connecting
- Keys stored with AES encryption

<!-- Screenshot placeholder: Session list -->
<!-- ![Session Management](../../screenshots/sessions.png) -->

---

## Cloud Host Sync

One-click discover hosts from multiple cloud platforms and auto-import them into the SSH session list — no manual entry needed.

### Supported Platforms

| Platform | Synced Content |
|----------|----------------|
| **Oracle Cloud (OCI)** | All instance public/private IPs, names, shapes, regions |
| **AWS** | EC2 instance public/private IPs, names (Name tag), instance types, regions |
| **Azure** | VM IP addresses and instance info |
| **SolusVM** | VPS node IP addresses |

### How It Works

1. Click the "Cloud Host Sync" button at the top of the host dashboard
2. The system queries all configured cloud platform Profiles in parallel
3. Real-time progress is displayed via SSE (Server-Sent Events) for each platform
4. Newly discovered hosts are automatically added to the host dashboard (existing IPs are skipped)
5. After sync completes, a summary shows added count, skipped count, and any errors

> Synced hosts default to SSH port 22, with automatic IPv6 address detection.

---

## OCI Object Storage Management

Manage OCI Object Storage directly from the web interface:

| Action | Description |
|--------|-------------|
| **Browse Buckets** | List all storage buckets |
| **Browse Objects** | Prefix filtering and pagination |
| **Upload Files** | Streaming upload with path traversal prevention |
| **Download Files** | Streaming download |
| **Delete Objects** | Delete individual files |
| **Create Folders** | Create directory structures |

<!-- Screenshot placeholder: OCI Object Storage interface -->
<!-- ![OCI Object Storage](../../screenshots/oss.png) -->

---

## SSL Certificate Configuration

### Built-in Self-Signed Certificate

The client ships with a self-signed PKCS12 certificate — works out of the box.

### ACME Auto-Certificate (Let's Encrypt)

Supports automatic issuance and renewal of Let's Encrypt certificates. Requirements:

1. A domain name pointing to your server
2. Port 80 accessible (for HTTP-01 verification)

Configure in the web interface under "Settings":

| Parameter | Description |
|-----------|-------------|
| **Domain/IP** | Domain to bind the certificate to |
| **Email** | Let's Encrypt notification email |
| **Challenge Port** | HTTP-01 verification port, default 80 |

Once configured, certificates are issued automatically and renewed 2 days before expiry.

---

## Multi-Language Support

The web interface supports Chinese/English switching via the language selector in the top bar.

- 简体中文 (zh-CN)
- English (en)

---

## Technical Specifications

| Item | Specification |
|------|---------------|
| Protocol | HTTPS (TLSv1.3) + WebSocket |
| Terminal | xterm.js |
| Max Connections | 200 concurrent |
| Max Message Size | 8 MB |
| Stale Connection Cleanup | 30-minute timeout with auto-reclaim |
| Download Transfer | 512 KB chunks + sliding window (4 windows) |
