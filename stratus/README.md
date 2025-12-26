# Stratus OS v1.0 (Kyronix)

Purpose: Secure NTP / Time Infrastructure Appliance  
Architecture: ARM64 (Raspberry Pi class devices)

---

## Flashing image

Linux / macOS:
```bash
gunzip -c stratus-os-v1.0-arm64.img.gz | sudo dd of=/dev/sdX bs=4M status=progress conv=fsync
