---
noIndex: true
icon: network-wired
cover: >-
  ../.gitbook/assets/[TIOF] Comms [P] 0000-00-00 TIOF - Page Header TechUp
  Community XXX v1.0.png
coverY: 0
layout:
  width: default
  cover:
    visible: true
    size: hero
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
---

# Network Access Requirements for PromptForge Server

## About

This document specifies the minimum outbound network access required for an Argos Club PromptForge server to operate correctly in side a Host Organization's (HO) network.

## General considerations

* Server: Debian running Proxmox VE 9.2
* No inbound ports are required on the HO's firewall.
* All remote access will use [Netbird](https://netbird.io/) and/or [Tailscale](https://tailscale.com/).

## Specifications

### 0. Parameters

| Parameter               | Value | Notes |
| ----------------------- | ----- | ----- |
| VPN Gateway MAC address |       |       |
| Server MAC address      |       |       |
| Others                  | N/A   | N/A   |

### 1. Basic Connectivity

* **DNS**: UDP/TCP port 53 outbound to HO's DNS servers or public resolvers (e.g., 8.8.8.8, 1.1.1.1).
* **NTP**: UDP port 123 outbound to `pool.ntp.org` or HO's time servers.
* **ICMP**: Limited outbound echo requests for diagnostics.

### 2. Operating System and Package Management

The server requires outbound access to Debian and Proxmox repositories for updates and package installation.

**Recommended sources.list entries (Proxmox 9.2 / Bookworm):**

```bash
deb http://deb.debian.org/debian bookworm main contrib
deb http://deb.debian.org/debian bookworm-updates main contrib
deb http://security.debian.org/debian-security bookworm-security main contrib

# Proxmox no-subscription repository
deb http://download.proxmox.com/debian/pve bookworm pve-no-subscription
```

**Required outbound access:**

* TCP ports 80 and 443 to:
  * `deb.debian.org`
  * `security.debian.org`
  * `download.proxmox.com`

### 3. Remote Management – Comet GL-RM1 IP KVM

* TCP 80/443 outbound for device management and cloud binding (if used).
* Connectivity to be achieved via Netbird/Tailscale.

#### 4. Proxmox VE Web Interface and Operation

* Access remotely via Tailscale/Netbird only.
* VM networking: HO's network configuration must allow VMs outbound access for their own Netbird/Tailscale clients.

### 5. Netbird (Host + VMs)

Netbird client must be able to connect outbound to TIOF's self-hosted instance at **Mesh.TheIOFoundation.org** (standard ports).

**Outbound rules:**

* TCP 443 to `Mesh.TheIOFoundation.org` (management, signal and dashboard).
* UDP 3478 to `Mesh.TheIOFoundation.org` (STUN/TURN).

### 6. Tailscale (Host + VMs)

Tailscale requires only outbound connections. No inbound ports.

**Outbound rules:**

* TCP 443 to `*.tailscale.com` and `*.ts.net` (control plane and DERP relays).
* UDP 41641 outbound to any destination (WireGuard).
* UDP 3478 outbound (STUN).
* TCP 80 outbound (occasional).

### **7. Authentik**

TIOF's self-hosted Identity Provider (IdP) will be Authentik, running at https://ID.TheIOFoundation.org (deployment in progress).

**Outbound rules:**

* TCP 443 to `ID.TheIOFoundation.org`.

### 8. Let's Encrypt

To issue and renew certificates with Let's Encrypt (via Certbot, acme.sh, or Proxmox built-in ACME):

**Outbound rules:**

* **TCP port 443** outbound to Let's Encrypt ACME servers.
* Primary domain: acme-v02.api.letsencrypt.org (and staging: acme-staging-v02.api.letsencrypt.org for testing).

{% hint style="info" %}
## PLEASE NOTE

Let's Encrypt does **not** publish fixed IP ranges — whitelist by **domain** where possible, or allow broad outbound HTTPS.
{% endhint %}

**Additional outbound needs:**

* **OCSP responders** (for certificate status checks): \*.o.lencr.org (e.g., r3.o.lencr.org, r10.o.lencr.org etc.).
* DNS resolution (port 53) for the above domains.

### 9. OMADA TP-Link ER706W VPN Gateway

The ER706W gateway adopts to the self-hosted Omada Controller at OMADA.TheIOFoundation.org.

**Required outbound access from the ER706W (and server behind it):**

* TCP 443 to OMADA.TheIOFoundation.org (HTTPS management / inform).
* UDP 29810 to OMADA.TheIOFoundation.org (device discovery).
* TCP 29814 to OMADA.TheIOFoundation.org (adoption and management, Omada v5+).
* TCP 29815–29816 to OMADA.TheIOFoundation.org (additional management, stats, remote terminal – recommended).
* Firmware updates: TCP 80/443 to download.tplinkcloud.com.

### 10. Summary of Required Outbound Destinations

<table><thead><tr><th>Service</th><th width="103.4444580078125">Protocol</th><th width="93.22216796875">Ports</th><th>Destinations</th><th>Notes</th></tr></thead><tbody><tr><td>DNS</td><td>UDP/TCP</td><td>53</td><td>HO's DNS or 8.8.8.8 / 1.1.1.1</td><td>Required for all name resolution</td></tr><tr><td>NTP</td><td>UDP</td><td>123</td><td>pool.ntp.org or HO's NTP</td><td>Time sync</td></tr><tr><td>Debian / Proxmox Updates</td><td>TCP</td><td>80, 443</td><td><ul><li>deb.debian.org</li><li>security.debian.org</li><li>download.proxmox.com</li></ul></td><td>Package management</td></tr><tr><td>Comet GL-RM1 KVM</td><td>TCP</td><td>80, 443</td><td>GL.iNet endpoints</td><td>Device management</td></tr><tr><td>Proxmox GUI</td><td>TCP</td><td>8006</td><td>Local (via Tailscale/Netbird)</td><td>Web admin</td></tr><tr><td>Tailscale</td><td>TCP</td><td>443</td><td>*.tailscale.com, *.ts.net</td><td>Control + relays</td></tr><tr><td>Tailscale</td><td>UDP</td><td>41641, 3478</td><td>Any</td><td>WireGuard + STUN</td></tr><tr><td>Netbird + Authentik</td><td>TCP</td><td>443</td><td><ul><li>Mesh.TheIOFoundation.org</li><li>ID.TheIOFoundation.org</li></ul></td><td>Management &#x26; auth</td></tr><tr><td>Netbird</td><td>UDP</td><td>3478 + TURN range</td><td><ul><li>Mesh.TheIOFoundation.org</li></ul></td><td>Peer connections</td></tr><tr><td>Let's Encrypt ACME</td><td>TCP</td><td>443</td><td><ul><li>acme-v02.api.letsencrypt.org</li><li>*.o.lencr.org</li></ul></td><td>Certificate issuance &#x26; renewal</td></tr><tr><td>OMADA Controller</td><td>TCP</td><td>443</td><td><ul><li>OMADA.TheIOFoundation.org</li></ul></td><td>HTTPS / Inform URL</td></tr><tr><td>OMADA Controller</td><td>UDP</td><td>29810</td><td><ul><li>OMADA.TheIOFoundation.org</li></ul></td><td>Discovery</td></tr><tr><td>OMADA Controller</td><td>TCP</td><td>29814–29816</td><td><ul><li>OMADA.TheIOFoundation.org</li></ul></td><td>Adoption, management, stats</td></tr></tbody></table>

## Contact

For any questions or further clarifications, please contact us at JFQueralt@TheIOFoundation.org





