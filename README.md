> **VeriMox is free, because data integrity should never be a luxury.**  
> Whether you're an MSP, school, nonprofit, enterprise, or solo developer — no one should lose data simply because they couldn’t afford a commercial tool.  
> Everyone deserves the ability to verify their backups and protect their systems with confidence.  
> If VeriMox helps even one person avoid a catastrophic restore failure, it has done its job.

---

## Overview

**VeriMox** is a lightweight disaster recovery verification utility for **Proxmox Backup Server (PBS)**.

It automatically restores the latest VM backup, boots the restored VM in isolation, captures a screenshot (e.g. Windows login screen), and optionally uploads the result to a FastAPI backend or dashboard.

To ensure the integrity of verification, VeriMox also performs **SHA hash checking on screenshots** — ensuring each verification is truly unique and not a false positive caused by a recycled snapshot.

This project is being released as an open-source module once it reaches a stable beta.  
It was originally extracted from a larger internal infrastructure automation platform to benefit the wider community.

---

## ✅ Purpose

VeriMox helps sysadmins and MSPs ensure that:

- PBS backups are restorable
- VMs boot successfully to the OS login screen
- Visual proof is captured for compliance or audits
- Duplicate or stale restores are detected via SHA hashing

---

## ⚙️ Features

- Ansible-driven restore, boot, screenshot, and cleanup workflow
- Supports both cron and API-triggered execution
- Screenshot capture via `qm screenshot`
- Optional FastAPI upload for dashboard integration
- SHA-256 hash verification to detect repeated screenshots
- No agents or open ports required on the guest VM

---

## 📦 Components

- `ansible/verify_pbs_backup.yml` – Main verification playbook
- `fastapi/main.py` – Screenshot upload endpoint (optional)
- `scripts/install_cron.sh` – Weekly test restore scheduler
- `docs/usage.md` – Setup and configuration instructions

---

## 🧰 Requirements

- Proxmox VE node with PBS access
- Ansible 2.10 or later
- Python 3.10+ (only if using FastAPI)
- Optional: cron or scheduler for automation

---

## 🔄 Example Workflow

1. Ansible selects latest backup from PBS
2. Restores it to a temporary VM ID (e.g. 9000)
3. Boots the VM and waits for the OS to load
4. Captures a screenshot from the Proxmox host
5. Calculates a SHA-256 hash of the screenshot
6. Uploads the screenshot or stores it locally
7. Destroys the temporary test VM
8. Dashboards or emails summarize verification results

---

## 📜 License

Licensed under the MIT License.  
Free for personal, academic, nonprofit, or commercial use.

---

