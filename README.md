# VeriMox

**Visual Backup Verification for Proxmox Backup Server (PBS)**  
Created and maintained by **Patrick Woodlock**

> **VeriMox is free, because data integrity should never be a luxury.**  
> Whether you're an MSP, a school, a healthcare provider, or a solo developer — backups must work.  
> This tool helps ensure that by automatically restoring Proxmox backups, booting the VMs, and capturing visual proof they actually function.

---

VeriMox is a disaster recovery verification utility for Proxmox PBS.  
It restores the latest VM backups, boots them in isolation, captures a screenshot (e.g. Windows login screen), and optionally uploads that image to a FastAPI endpoint or dashboard for audit tracking.

To prevent false positives or repeated snapshots from being misinterpreted as valid, **VeriMox includes SHA hashing of screenshots** to detect duplicate images. This ensures that each verification is genuinely unique — not just a recycled result from a stale restore.

This module is being released as a standalone open-source project once it reaches a stable beta stage.  
It was extracted from a larger internal infrastructure platform to serve the wider community — because **no system is truly protected until a restore is verified and proven to boot.**

---

## Purpose

VeriMox helps MSPs and sysadmins confirm that:

- PBS backups are restorable
- VMs boot correctly to the login screen
- Visual proof is available for compliance or DR assurance

---

## Features

- Ansible-driven restore and cleanup process
- Boot and pause logic for temporary VMs
- Screenshot capture using `qm screenshot`
- FastAPI-based upload endpoint (optional)
- Supports cron-based scheduling (e.g. weekly tests)
- No agents or ports required

---

## Components

- `ansible/verify_pbs_backup.yml` – Main playbook
- `fastapi/main.py` – Upload receiver (optional)
- `scripts/install_cron.sh` – Weekly test restore scheduler
- `docs/usage.md` – Setup and configuration guidance

---

## Requirements

- Proxmox VE node with PBS access
- Ansible (2.10+)
- Python 3.10+ (if using FastAPI upload)
- Cron or external scheduler (optional)

---

## Example Use Case

1. Restore latest PBS VM to temporary ID
2. Start and wait for OS boot
3. Capture screenshot
4. Upload screenshot or store locally
5. Destroy temporary VM
6. Review screenshots weekly via your dashboard

---

## License

Licensed under the MIT License.  
Free for private and commercial use.

---


