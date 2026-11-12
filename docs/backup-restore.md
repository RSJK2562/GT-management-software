# GT Management Software — Backup & Disaster Recovery Guide

## Overview
GT Management Software provides automated and on-demand database snapshots stored in protected directories (`/storage/backups/`).

---

## 1. Creating an Instant Backup
1. Sign in as the **Business Owner** (`owner@gt.com`).
2. Navigate to **Settings** &rarr; **Backup & Reset**.
3. Click **Create Backup Now**.
4. The system will compile a timestamped SQL dump (e.g. `GT_backup_20261027_150000.sql`) containing:
   - Businesses, Customers, Products, Leads, Tasks
   - Quotations & Invoices (with historical snapshots)
   - Payments & Allocations
   - Expenses & Categories
   - Activity Audit Trail

---

## 2. Restoring a Backup
Backups can be restored directly through the SQL client or via `RestoreService`:
```powershell
Get-Content "storage/backups/GT_backup_YYYYMMDD_HHMMSS.sql" | c:\xampp\mysql\bin\mysql.exe -u root gt_management
```

---

## 3. Resetting to Factory Demo State
To restore baseline test data:
1. Navigate to **Settings** &rarr; **Backup & Reset**.
2. Click **Reset to Factory Demo State** in the danger zone.
3. All default demonstration entities will be re-seeded.
