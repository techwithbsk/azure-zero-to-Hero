# Azure Storage Account Security

# Private Endpoint vs Service Endpoint

## Overview

In this lab, you'll learn how to secure an Azure Storage Account using **Service Endpoint** and **Private Endpoint**.

We'll deploy:

- Resource Group
- Virtual Network
- Subnet
- Windows/Linux VM
- Storage Account
- Service Endpoint
- Private Endpoint
- Private DNS Zone

Finally, we'll verify connectivity from the Azure VM.

---

# Lab Architecture

```text
                    Azure Subscription
                           │
                    Resource Group
                           │
          ┌────────────────┴────────────────┐
          │                                 │
      Storage Account                 Virtual Network
          │                                  │
          │                          Subnet-01
          │                                  │
          │                              Azure VM
          │                                  │
   ┌──────┴─────────┐                        │
   │                │                        │
Service Endpoint   Private Endpoint──────────┘
                        │
                 Private DNS Zone
```

---

# Objectives

- Create Azure Storage Account
- Create Azure Virtual Network
- Create Azure VM
- Configure Service Endpoint
- Configure Private Endpoint
- Configure Private DNS
- Verify Connectivity
- Compare Both Solutions

---

# Prerequisites

- Azure Subscription
- Resource Group
- Basic Azure Networking Knowledge

---

# Resources Created

| Resource | Example Name |
|-----------|--------------|
| Resource Group | RG-Storage-Lab |
| Storage Account | sttechwithbskdemo |
| Virtual Network | VNET-Storage |
| Subnet | Subnet-App |
| Virtual Machine | VM-App01 |
| Private Endpoint | PE-Storage |
| Private DNS Zone | privatelink.blob.core.windows.net |

---

# Step 1 - Create Resource Group

Azure Portal

```
Resource Groups

↓

Create
```

Example

```
RG-Storage-Lab
```

---

# Step 2 - Create Virtual Network

Navigate

```
Virtual Network

↓

Create
```

Configuration

```
Name

VNET-Storage
```

Address Space

```
10.0.0.0/16
```

Subnet

```
Subnet-App

10.0.1.0/24
```

---

# Step 3 - Create Virtual Machine

Navigate

```
Virtual Machines

↓

Create
```

Configuration

```
VM Name

VM-App01
```

OS

```
Windows Server 2022

or

Ubuntu 24.04
```

Network

```
VNET-Storage

Subnet-App
```

Deploy the VM successfully.

---

# Step 4 - Create Storage Account

Navigate

```
Storage Accounts

↓

Create
```

Configuration

```
Name

sttechwithbskdemo
```

Performance

```
Standard
```

Redundancy

```
LRS
```

Finish deployment.

---

# Part 1 - Service Endpoint

---

## Step 5 - Enable Service Endpoint

Navigate

```
Virtual Network

↓

Subnet-App

↓

Service Endpoints
```

Select

```
Microsoft.Storage
```

Save.

---

## Step 6 - Configure Storage Firewall

Navigate

```
Storage Account

↓

Networking
```

Choose

```
Selected Networks
```

Add

```
VNET-Storage

Subnet-App
```

Save.

---

## Step 7 - Verify Service Endpoint

Login to VM.

Run

Windows

```powershell
nslookup sttechwithbskdemo.blob.core.windows.net
```

Linux

```bash
nslookup sttechwithbskdemo.blob.core.windows.net
```

Result

```
Public IP
```

Although DNS resolves to a public IP, traffic travels securely over Microsoft's backbone network because the subnet has a Service Endpoint enabled.

---

# Part 2 - Private Endpoint

---

## Step 8 - Create Private Endpoint

Navigate

```
Storage Account

↓

Networking

↓

Private Endpoint Connections

↓

Create
```

Configuration

```
Name

PE-Storage
```

Virtual Network

```
VNET-Storage
```

Subnet

```
Subnet-App
```

Resource

```
Blob
```

---

## Step 9 - Private DNS Zone

Enable

```
Integrate with Private DNS Zone
```

Azure creates

```
privatelink.blob.core.windows.net
```

automatically.

---

## Step 10 - Disable Public Access

Navigate

```
Storage Account

↓

Networking
```

Choose

```
Disable Public Network Access
```

Save.

---

## Step 11 - Verify Private Endpoint

Login to VM.

Run

Windows

```powershell
nslookup sttechwithbskdemo.blob.core.windows.net
```

Linux

```bash
nslookup sttechwithbskdemo.blob.core.windows.net
```

Expected

```
10.x.x.x
```

The Storage Account now resolves to a **private IP**.

---

# Verify Blob Access

Upload a sample file.

Open Storage Account

↓

Containers

↓

Create

Example

```
images
```

Upload

```
sample.jpg
```

From the VM, browse to the Blob URL.

The request succeeds through the Private Endpoint.

---

# Service Endpoint vs Private Endpoint

| Feature | Service Endpoint | Private Endpoint |
|----------|-----------------|------------------|
| Public Endpoint | ✅ Yes | ❌ No |
| Private IP | ❌ No | ✅ Yes |
| Uses Azure Backbone | ✅ Yes | ✅ Yes |
| Private DNS | ❌ No | ✅ Yes |
| Internet Exposure | Public Endpoint Exists | Fully Private |
| Security | High | Very High |
| Production Recommendation | Good | Best Practice |

---

# Verification Commands

## Windows

```powershell
nslookup sttechwithbskdemo.blob.core.windows.net
```

---

## Linux

```bash
nslookup sttechwithbskdemo.blob.core.windows.net
```

---

## Test Storage Access

```bash
curl https://sttechwithbskdemo.blob.core.windows.net
```

---

# Best Practices

- Use Private Endpoint for production workloads.
- Disable Public Network Access whenever possible.
- Enable Private DNS integration.
- Restrict Storage Firewall to trusted networks.
- Use RBAC and Managed Identities instead of storage keys.
- Enable Soft Delete and Versioning for Blob Storage.

---

# Real-World Use Cases

## Service Endpoint

- Development Environments
- Internal Azure Applications
- Cost-Optimized Deployments

## Private Endpoint

- Banking Applications
- Healthcare Systems
- Government Projects
- Enterprise Production Workloads
- Regulatory Compliance (PCI DSS, HIPAA, etc.)

---

# Interview Questions

### What is a Service Endpoint?

A Service Endpoint extends a Virtual Network's identity to Azure services while the service continues to use its public endpoint.

---

### What is a Private Endpoint?

A Private Endpoint assigns a private IP address from your VNet to an Azure service, enabling private connectivity.

---

### Which option is more secure?

Private Endpoint.

---

### Does a Service Endpoint remove the public endpoint?

No. The Storage Account still has a public endpoint.

---

### Why is a Private DNS Zone required?

It ensures the Storage Account FQDN resolves to the private IP address instead of the public endpoint.

---

# Conclusion

In this lab, we successfully:

- Created a Virtual Network
- Created an Azure VM
- Created a Storage Account
- Configured Service Endpoint
- Configured Private Endpoint
- Configured Private DNS
- Verified connectivity from the Azure VM
- Compared Service Endpoint and Private Endpoint

You now understand how to securely access Azure Storage using Microsoft's recommended networking options.


---

# Author

**TechWithBSK**

Sai Krishna Basam

DevOps & Cloud Engineer

Azure | AWS | Kubernetes | Terraform | Azure DevOps

⭐ If this repository helped you, don't forget to **Star** it and subscribe to the **TechWithBSK** YouTube channel!