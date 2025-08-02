# VeriMox

**Visual Backup Verification for Proxmox Backup Server (PBS)**  
Created and maintained by **Patrick Woodlock**

> **VeriMox is free, because data integrity should never be a luxury.**  
> Data loss affects everyone — individuals, schools, nonprofits, and enterprises alike.  
> Reliable backups aren't enough; they must be testable and restorable. VeriMox helps make that possible.  
> If this tool prevents even one critical restore failure, then it has served its purpose.

---

## Overview

**VeriMox** is a lightweight disaster recovery verification utility for **Proxmox Backup Server (PBS)**.

It automatically restores the latest VM backup, boots the restored VM in isolation, captures a screenshot (e.g. Windows login screen), and optionally uploads the result to a FastAPI backend or dashboard for visual auditing.

To ensure integrity and prevent false positives, VeriMox performs **SHA-256 hashing of screenshots**, confirming that each restore is a unique, valid result — not a repeated or stale image.

This project will be released as open source once it reaches a stable beta stage.  
It was originally developed as part of a broader infrastructure automation system and is now shared with the wider community.

---

## ✅ Purpose

VeriMox helps sysadmins and MSPs ensure that:

- PBS backups are restorable
- VMs boot successfully to the OS login screen
- Visual proof is captured for compliance and DR audits
- Duplicate or stale restores are detected via SHA hashing

---

## ⚙️ Features

- Ansible-driven restore, boot, screenshot, and cleanup workflow
- Supports both cron and API-triggered execution
- Screenshot capture via `qm screenshot`
- Optional FastAPI upload for dashboard integration
- SHA-256 hash verification to detect repeated results
- No agents or open guest VM ports required

---

## 📦 Components

- `ansible/verify_pbs_backup.yml` – Main verification playbook
- `fastapi/main.py` – Screenshot upload endpoint (optional)
- `scripts/install_cron.sh` – Weekly test restore scheduler
- `docs/usage.md` – Setup and configuration guide

---

## 🧰 Requirements

- Proxmox VE node with PBS access
- Ansible 2.10+ (YAML playbooks)
- Python 3.10+ (if using FastAPI)
- Optional: cron job or external scheduler

---

## 🔄 Example Workflow

1. Ansible selects the latest backup from PBS
2. Restores it to a temporary VM ID (e.g. 9000)
3. Boots the VM and waits for OS to load
4. Captures a screenshot from the Proxmox host
5. Computes a SHA-256 hash of the screenshot
6. Uploads the screenshot or stores it locally
7. Destroys the temporary test VM
8. Optional dashboard displays or emails results

---

## 📜 License

Licensed under the MIT License.  
Free for personal, academic, nonprofit, or commercial use.

---
