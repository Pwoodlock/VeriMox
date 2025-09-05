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

## 📜 License

Licensed under the MIT License.  
Free for personal, academic, nonprofit, or commercial use.

---
