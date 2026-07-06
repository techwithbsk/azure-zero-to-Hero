# Azure Storage Account - Part 3

# Access Keys, Azure File Share, Queue Storage & Table Storage

## Overview

This lab demonstrates the remaining core services of Azure Storage Account:

- Storage Access Keys
- Azure File Share
- Azure Queue Storage
- Azure Table Storage

These services are widely used for authentication, shared storage, asynchronous messaging, and NoSQL data storage in enterprise cloud environments.

---

# Lab Architecture

```text
                    Azure Storage Account
                             │
      ┌──────────────┬───────────────┬───────────────┐
      ▼              ▼               ▼               ▼
 Access Keys     File Share     Queue Storage   Table Storage
      │              │               │               │
Authentication   Shared Files   Messaging      NoSQL Database
```

---

# Objectives

- Understand Storage Access Keys
- Create Azure File Share
- Upload Files
- Create Queue Storage
- Send & Receive Messages
- Create Azure Table
- Store NoSQL Data
- Learn Enterprise Use Cases

---

# Prerequisites

- Azure Subscription
- Resource Group
- Storage Account
- Azure Portal Access

---

# Step 1 - Create Storage Account

Navigate

```
Storage Accounts

↓

Create
```

Example

```
sttechwithbskdemo
```

---

# Part 1 - Storage Access Keys

## What are Access Keys?

Azure Storage provides two access keys that allow applications and users to authenticate and access storage resources.

Navigate

```
Storage Account

↓

Security + Networking

↓

Access Keys
```

You will see:

- Key1
- Key2
- Connection String

> **Best Practice:** Rotate keys regularly and prefer Microsoft Entra ID (Azure AD) or Managed Identity for production workloads instead of access keys.

---

# Part 2 - Azure File Share

## What is Azure File Share?

Azure File Share provides fully managed SMB and NFS file shares that can be mounted on Azure VMs, on-premises servers, or client machines.

Navigate

```
Storage Account

↓

File Shares

↓

Create
```

Example

```
sharedfiles
```

---

## Upload Files

Upload:

- Documents
- Images
- Backup Files

Verify successful upload.

---

## Mount Azure File Share

Windows

```powershell
net use Z: \\sttechwithbskdemo.file.core.windows.net\sharedfiles
```

Linux

```bash
sudo mount -t cifs //sttechwithbskdemo.file.core.windows.net/sharedfiles /mnt/fileshare
```

---

# Part 3 - Queue Storage

## What is Queue Storage?

Queue Storage stores messages that enable asynchronous communication between application components.

Navigate

```
Storage Account

↓

Queues

↓

Create Queue
```

Example

```
orderqueue
```

---

## Add Message

```
Order Received

↓

Payment Pending

↓

Processing Complete
```

Applications can retrieve and process these messages independently.

---

# Part 4 - Table Storage

## What is Table Storage?

Azure Table Storage is a NoSQL key-value store used for storing large amounts of structured, non-relational data.

Navigate

```
Storage Account

↓

Tables

↓

Create Table
```

Example

```
EmployeeDetails
```

---

## Sample Data

| PartitionKey | RowKey | Name | Department |
|--------------|--------|------|------------|
| EMP | 1001 | Sai Krishna | DevOps |
| EMP | 1002 | John | Cloud |

---

# Security Best Practices

- Use Microsoft Entra ID where possible
- Rotate Storage Access Keys
- Enable Private Endpoints
- Enable Soft Delete
- Enable Blob Versioning
- Restrict Public Access
- Use RBAC for access control

---

# Real-World Use Cases

## Access Keys

- Application Authentication
- Legacy Applications

## Azure File Share

- Shared File Storage
- Lift & Shift File Servers
- Team Collaboration

## Queue Storage

- Order Processing
- Notification Systems
- Background Jobs
- Microservices Communication

## Table Storage

- User Profiles
- Device Metadata
- Inventory Data
- Configuration Storage
- IoT Solutions

---

# Interview Questions

### What are Azure Storage Access Keys?

Authentication keys used to access Storage Account resources.

---

### How many access keys are available?

Two (Key1 and Key2).

---

### What protocol does Azure File Share support?

SMB and NFS.

---

### What is Azure Queue Storage used for?

Reliable message storage for asynchronous communication.

---

### What is Azure Table Storage?

A NoSQL key-value store for structured, non-relational data.

---

### Which service should be used to store application messages?

Azure Queue Storage.

---

### Which service should be used for shared files?

Azure File Share.

---

### Which service should be used for NoSQL structured data?

Azure Table Storage.

---

# Next Video

Azure Storage Account Part 4

- Shared Access Signature (SAS)
- Storage Explorer
- Lifecycle Management
- Immutable Storage
- Versioning & Soft Delete

---

# Author

**TechWithBSK**

Sai Krishna Basam

DevOps & Cloud Engineer

Azure | AWS | Kubernetes | Terraform | Azure DevOps

⭐ If this repository helped you, don't forget to **Star** it and subscribe to the **TechWithBSK** YouTube channel!

Happy Learning! 🚀