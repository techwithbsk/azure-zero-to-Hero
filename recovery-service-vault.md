# Azure Recovery Services Vault

# Azure Backup & Azure Site Recovery (ASR)

## Overview

Azure Recovery Services Vault is a centralized service that enables backup, disaster recovery, and business continuity for Azure workloads and on-premises environments.

In this lab, you'll learn how to configure Azure Backup and Azure Site Recovery (ASR) for Azure Virtual Machines.

---

# Lab Architecture

```text
                    Azure Subscription
                            │
                    Resource Group
                            │
             Azure Recovery Services Vault
                    │                  │
        Azure Backup            Azure Site Recovery
              │                        │
       Backup Policy             Replication Policy
              │                        │
        Azure Virtual Machine   Secondary Region
              │                        │
      Restore Points         Failover / Failback
```

---

# Objectives

- Create Recovery Services Vault
- Configure Azure Backup
- Create Backup Policy
- Enable VM Backup
- Restore Azure VM
- Configure Azure Site Recovery
- Replicate Azure VM
- Perform Test Failover
- Perform Planned Failover
- Understand Disaster Recovery

---

# Prerequisites

- Azure Subscription
- Resource Group
- Azure Virtual Machine
- Virtual Network

---

# Resources

| Resource | Example Name |
|----------|--------------|
| Resource Group | RG-Backup-Lab |
| Recovery Services Vault | RSV-TechWithBSK |
| Virtual Machine | VM-App01 |
| Backup Policy | DailyBackup |
| Replication Policy | ASR-Policy |

---

# Part 1 - Azure Backup

## Step 1 - Create Recovery Services Vault

Navigate

```
Azure Portal

↓

Recovery Services Vault

↓

Create
```

Example

```
RSV-TechWithBSK
```

---

## Step 2 - Configure Backup

Navigate

```
Recovery Services Vault

↓

Backup

↓

Azure Virtual Machine
```

---

## Step 3 - Create Backup Policy

Example

```
Daily Backup

Time : 10 PM

Retention : 30 Days
```

---

## Step 4 - Enable Backup

Select

```
VM-App01
```

Enable protection.

---

## Step 5 - Trigger Backup

Click

```
Backup Now
```

Monitor backup job completion.

---

## Step 6 - Restore VM

Navigate

```
Recovery Services Vault

↓

Backup Items

↓

Azure VM

↓

Restore VM
```

Choose a restore point and initiate the restore process.

---

# Part 2 - Azure Site Recovery (ASR)

## What is Azure Site Recovery?

Azure Site Recovery continuously replicates virtual machines to another Azure region or recovery site.

It minimizes downtime during disasters by enabling automated failover and failback.

---

## Step 7 - Enable Site Recovery

Navigate

```
Recovery Services Vault

↓

Site Recovery

↓

Enable Replication
```

---

## Step 8 - Configure Replication

Source

```
Primary Region
```

Target

```
Secondary Region
```

Replication Policy

```
ASR-Policy
```

---

## Step 9 - Start Replication

Azure begins replicating VM disks and configuration to the target region.

Monitor replication health.

---

## Step 10 - Test Failover

Navigate

```
Recovery Services Vault

↓

Replicated Items

↓

Test Failover
```

Verify the replicated VM starts successfully.

---

## Step 11 - Planned Failover

Use Planned Failover for maintenance or migration with minimal downtime.

---

## Step 12 - Unplanned Failover

Use Unplanned Failover during outages or disasters.

---

## Step 13 - Failback

Once the primary region is available, perform Failback to resume normal operations.

---

# Backup vs Site Recovery

| Feature | Azure Backup | Azure Site Recovery |
|----------|--------------|---------------------|
| Purpose | Data Protection | Disaster Recovery |
| Restore Files | Yes | No |
| VM Recovery | Yes | Yes |
| Replication | No | Yes |
| Failover | No | Yes |
| Failback | No | Yes |
| Business Continuity | Partial | Full |

---

# Best Practices

- Enable daily backups for production VMs.
- Use Recovery Services Vault with soft delete enabled.
- Test restores regularly.
- Configure Site Recovery for mission-critical workloads.
- Perform periodic Test Failovers.
- Monitor backup and replication health.

---

# Real-World Use Cases

## Azure Backup

- Azure VM Backup
- Azure File Share Backup
- SQL Server Backup
- Long-Term Retention

## Azure Site Recovery

- Disaster Recovery
- Business Continuity
- Regional Outage Protection
- Data Center Migration
- Planned Maintenance

---

# Interview Questions

### What is Azure Recovery Services Vault?

A centralized Azure service used for backup and disaster recovery.

---

### What is Azure Backup?

A service that creates recovery points for Azure workloads.

---

### What is Azure Site Recovery?

A disaster recovery service that replicates workloads and enables failover during outages.

---

### What is the difference between Backup and Site Recovery?

Backup protects data and enables restoration, while Site Recovery replicates workloads to ensure business continuity during disasters.

---

### What is Failover?

Switching workloads to a secondary location when the primary environment becomes unavailable.

---

### What is Failback?

Returning workloads to the original primary environment after recovery.

---

# Next Video

Azure Monitor

- Azure Monitor
- Log Analytics
- Alerts
- Metrics
- Diagnostic Settings

---

# Author

**TechWithBSK**

Sai Krishna Basam

DevOps & Cloud Engineer

Azure | AWS | Kubernetes | Terraform | Azure DevOps

⭐ If this repository helped you, please **Star** the repository and subscribe to the **TechWithBSK** YouTube channel.

Happy Learning! 🚀