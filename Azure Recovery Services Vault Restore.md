# Azure Recovery Services Vault Restore

## Backup Restore & Site Recovery (ASR) Restore

### Overview

This lab demonstrates how to restore Azure Virtual Machines using **Azure Recovery Services Vault** through two recovery methods:

- Azure Backup Restore
- Azure Site Recovery (ASR)

You'll learn how to restore virtual machines from recovery points, perform failover during disasters, and fail back to the primary region.

---

## Lab Architecture

```text
                  Recovery Services Vault
                         │
        ┌────────────────┴──────────────┐
        ▼                               ▼
   Azure Backup                  Azure Site Recovery
        │                               │
  Recovery Points                VM Replication
        │                               │
 Restore VM                    Secondary Region
        │                               │
 Restore Files               Failover & Failback
```

---

## Objectives

- Restore Azure VM from Backup
- Restore Individual Files
- Restore Managed Disks
- Create New VM from Backup
- Perform Test Failover
- Perform Planned Failover
- Perform Unplanned Failover
- Perform Failback
- Compare Backup vs Site Recovery

---

## Prerequisites

- Azure Subscription
- Recovery Services Vault
- Azure Virtual Machine
- Site Recovery Replication Enabled

---

# Part 1 – Azure Backup Restore

## Step 1 – Open Recovery Services Vault

Navigate:

Azure Portal

↓

Recovery Services Vault

↓

Backup Items

↓

Azure Virtual Machine

Select your protected VM.

---

## Step 2 – View Recovery Points

Open:

```text
Recovery Points
```

You'll see multiple restore points based on your backup policy.

Example:

- Daily Backup
- Weekly Backup
- Monthly Backup

---

## Step 3 – Restore Azure VM

Choose:

```text
Restore VM
```

Available options:

- Create New VM
- Restore Disks
- Replace Existing VM

For safety, choose:

```text
Create New VM
```

Azure creates a new VM using the selected recovery point.

---

## Step 4 – Restore Disks

Select:

```text
Restore Disks
```

Azure restores managed disks without creating a VM.

Useful when:

- VM configuration is damaged.
- Only disks need recovery.

---

## Step 5 – Restore Files

Select:

```text
File Recovery
```

Azure provides a temporary script to mount the recovery point.

Example (Linux):

```bash
chmod +x VMRestore.sh
sudo ./VMRestore.sh
```

Browse mounted files and recover only the required data.

---

# Part 2 – Azure Site Recovery Restore

## Step 6 – Open Site Recovery

Navigate:

```text
Recovery Services Vault

↓

Site Recovery

↓

Replicated Items
```

Select the replicated VM.

---

## Step 7 – Test Failover

Choose:

```text
Test Failover
```

Purpose:

- Validate Disaster Recovery
- No production impact
- Verify application functionality

Azure creates a temporary replica VM.

---

## Step 8 – Planned Failover

Use Planned Failover for:

- Maintenance
- Migration
- Controlled Failover

Traffic moves to the secondary region with minimal downtime.

---

## Step 9 – Unplanned Failover

Use when:

- Primary region is unavailable.
- Disaster occurs.
- Production outage happens.

Azure immediately starts the replica VM.

---

## Step 10 – Commit Failover

After confirming workloads are healthy:

```text
Commit
```

The secondary region becomes the active production environment.

---

## Step 11 – Failback

Once the primary region is available:

Choose:

```text
Failback
```

Azure:

- Synchronizes changes.
- Replicates data back.
- Restores production to the primary region.

---

# Backup Restore vs Site Recovery

| Feature | Azure Backup | Azure Site Recovery |
|----------|--------------|---------------------|
| Restore Files | Yes | No |
| Restore VM | Yes | Yes |
| Recovery Points | Yes | No |
| Continuous Replication | No | Yes |
| Failover | No | Yes |
| Failback | No | Yes |
| Disaster Recovery | Partial | Full |

---

# Verification Checklist

After Backup Restore:

- VM starts successfully.
- Applications are accessible.
- Data is intact.

After Site Recovery:

- Replica VM starts.
- Network connectivity works.
- Applications function correctly.
- Failback completes successfully.

---

# Best Practices

- Test restores regularly.
- Enable soft delete.
- Keep multiple recovery points.
- Perform Test Failover periodically.
- Monitor replication health.
- Document DR procedures.

---

# Real-World Scenarios

### Backup Restore

- Accidental VM deletion
- File corruption
- Disk recovery
- Ransomware recovery

### Site Recovery

- Regional outages
- Disaster Recovery
- Planned maintenance
- Business Continuity

---

# Interview Questions

### What is the difference between Backup Restore and Site Recovery?

Backup restores data from recovery points, while Site Recovery continuously replicates workloads for disaster recovery.

### What is Test Failover?

A non-disruptive validation of the Disaster Recovery environment.

### What is Planned Failover?

A controlled migration with minimal downtime.

### What is Unplanned Failover?

An emergency failover during outages.

### What is Failback?

Moving workloads back to the original primary region after recovery.

---

# Author

**TechWithBSK**

Sai Krishna Basam

Azure | AWS | Kubernetes | Terraform | Azure DevOps

Happy Learning! 🚀