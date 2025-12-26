# Stratus OS v1.0 (Kyronix)

[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/X8X31QYP4A)

![Platform](https://img.shields.io/badge/Platform-ARM64-blue)
![Hardware](https://img.shields.io/badge/Hardware-Raspberry%20Pi-lightgrey)
![Service](https://img.shields.io/badge/Service-NTP%20Appliance-orange)
![Init](https://img.shields.io/badge/Init-systemd-informational)
![License](https://img.shields.io/badge/License-MIT-green)
![Status](https://img.shields.io/badge/Build-Stable-success)

---

## 🕒 Overview

**Stratus OS** is a **minimal, hardened ARM64 Linux appliance** designed exclusively for **secure and deterministic time infrastructure**.

It is built as a **single-purpose NTP appliance**, optimized for reliability, security, and predictability in both **enterprise and isolated environments**.

Project by **Kyronix**.

---

## 🎯 Design Philosophy

- 🔒 Security-first, minimal attack surface
- ⏱️ Deterministic and reproducible boot
- 🧠 One role → one system
- 🧼 Clean filesystem & service layout
- 💾 Universal SD card image (8GB+)

---

## 🧱 Architecture

### Logical Time Topology

```text
        ┌──────────────┐
        │  GPS / PPS   │
        │  (Optional)  │
        └──────┬───────┘
               │
        ┌──────▼───────┐
        │  Stratus OS  │  ← Stratum-1
        │  (chrony)   │
        └──────┬───────┘
               │
     ┌─────────▼─────────┐
     │ Internal Network  │
     │ Servers / Clients │
     └───────────────────┘
```
## 🧱 System Architecture

- **CPU:** ARM64 (AArch64)
- **Init:** systemd
- **Time daemon:** chrony
- **Access:** SSH only - first login with password (user: root, password: admin)
- **Package scope:** minimal (no desktop, no UI)

---

## 🔧 Included Services

| Service  | Purpose |
|--------|--------|
| chrony | NTP server / client |
| SSH    | Secure remote management |
| systemd | Boot & service control |

---

## 🔐 Security & Hardening

Stratus OS follows a **deny-by-default** security model.

### Implemented

- Minimal userspace
- No web services
- No package manager exposed
- SSH-only management
- Deterministic service startup
- Predictable filesystem layout

### Recommended (Deployment)

- Change SSH keys on first boot
- Restrict SSH to management VLAN
- Firewall NTP (UDP 123) only
- Disable password authentication
- Use PPS/GPS only on trusted hardware

---

## 💾 Flashing the Image

### Linux / macOS

```bash
gunzip -c stratus-os-v1.0-arm64.img.gz | sudo dd of=/dev/sdX bs=4M status=progress conv=fsync
```
⚠️ Replace /dev/sdX with your actual SD card device.

## 🧰 Recommended Hardware

- Raspberry Pi **3 / 4 / 5**
- **8 GB SD card minimum**
- Wired Ethernet (recommended)
- Optional: GPS + PPS module

---

## 📦 Use Cases

- 🏢 Enterprise internal time authority
- 🔒 Isolated / air-gapped networks
- 🧪 SOC, LAB, OT environments
- 🛰️ Stratum-1 (GPS/PPS)
- 🌐 Stratum-2 relay nodes

---

## ⚠️ Known Limitations (v1.0)

- ❌ No web UI
- ❌ No OTA updates
- ❌ Single-purpose appliance only

---

## 🛣️ Roadmap

### v1.1
- 🔄 OTA update mechanism
- 🔐 Key rotation helper
- 📡 Auto GPS/PPS detection

### v1.2+
- 🌐 Optional lightweight management UI
- 🧩 Modular service extensions
- 📊 Time health metrics export
- 🛰️ Multi-source failover

---

## 📄 License

Licensed under the **MIT License**.

---

## 🤝 Contributing

This project follows a **controlled appliance model**.  
Suggestions, issues, and discussions are welcome via **GitHub Issues**.




