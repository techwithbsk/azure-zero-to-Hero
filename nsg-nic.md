# 🔒 Azure Network Security Group (NSG) at NIC Level

## 📌 Overview

This project demonstrates how to configure an Azure Network Security Group (NSG) at the Network Interface Card (NIC) level to control inbound and outbound traffic for a specific Virtual Machine.

Applying NSG at the NIC level provides granular security control for individual Azure Virtual Machines.

---

# 🎯 Objectives

* Understand Azure Network Security Groups (NSG)
* Learn NSG rule processing
* Configure NSG at NIC level
* Create custom inbound and outbound rules
* Secure Azure Virtual Machines
* Test network connectivity

---

# 🏗 Architecture

```text
Internet
    │
    ▼
Virtual Machine
    │
    ▼
Network Interface (NIC)
    │
    ▼
Network Security Group (NSG)
```

Traffic Flow:

```text
User Request
      │
      ▼
     NSG
      │
      ▼
     NIC
      │
      ▼
      VM
```

---

# 📚 What is Azure NSG?

Azure Network Security Group (NSG) is a service used to filter and control network traffic to Azure resources.

NSGs allow:

✅ Allow Traffic

✅ Deny Traffic

✅ Inbound Security Rules

✅ Outbound Security Rules

✅ Traffic Filtering

---

# 🔥 NSG Association Levels

Azure NSG can be associated with:

## 1. Subnet Level

```text
Subnet
  │
  ├── VM1
  ├── VM2
  └── VM3
```

Rules apply to all resources in the subnet.

---

## 2. NIC Level

```text
VM
 │
NIC
 │
NSG
```

Rules apply only to that specific VM.

---

# 💡 Why Use NSG at NIC Level?

Benefits:

* Granular Security Control
* VM-Specific Access
* Enhanced Security
* Application Isolation
* Better Compliance

---

# ⚠ Prerequisites

Before starting:

* Azure Subscription
* Resource Group
* Virtual Network
* Subnet
* Virtual Machine
* Network Interface

---

# 🛠 Implementation Steps

## Step 1: Create Resource Group

```text
RG-NSG-DEMO
```

---

## Step 2: Create Virtual Network

```text
VNet: 10.0.0.0/16
Subnet: 10.0.1.0/24
```

---

## Step 3: Create Virtual Machine

Example:

```text
VM Name: vm-nsg-demo
OS: Windows/Linux
```

---

## Step 4: Create Network Security Group

Navigate:

```text
Azure Portal
→ Create Resource
→ Network Security Group
```

Example:

```text
NSG Name:
nsg-nic-demo
```

---

## Step 5: Associate NSG with NIC

Navigate:

```text
Virtual Machine
→ Networking
→ Network Interface
→ Network Security Group
```

Select:

```text
nsg-nic-demo
```

Save configuration.

---

# 🔒 Inbound Security Rules

Example Rule:

Allow SSH

```text
Priority : 100
Port     : 22
Protocol : TCP
Action   : Allow
```

---

Allow RDP

```text
Priority : 110
Port     : 3389
Protocol : TCP
Action   : Allow
```

---

Allow HTTP

```text
Priority : 120
Port     : 80
Protocol : TCP
Action   : Allow
```

---

# 🔒 Outbound Security Rules

Example:

Allow Internet Access

```text
Destination : Internet
Port        : Any
Action      : Allow
```

---

# 📊 NSG Rule Processing

Rules are processed based on Priority.

Example:

```text
Priority 100 → Allow SSH
Priority 110 → Allow RDP
Priority 120 → Allow HTTP
Priority 200 → Deny All
```

Lower number = Higher priority

---

# 🧪 Connectivity Testing

For Linux:

```bash
ssh azureuser@<Public-IP>
```

For Windows:

```powershell
mstsc
```

Verify:

* Allowed ports work
* Denied ports are blocked

---

# 🚀 Real-Time Use Cases

* Restrict RDP Access
* Restrict SSH Access
* Secure Production Servers
* Database Protection
* Application Isolation
* Compliance Requirements

---

# 🎯 Interview Questions

### What is Azure NSG?

Azure NSG is a network security service that controls inbound and outbound traffic using security rules.

---

### Can NSG be applied at NIC level?

Yes.

Azure supports:

* Subnet Level NSG
* NIC Level NSG

---

### Which NSG takes precedence?

Both NSGs are evaluated.

Traffic must be allowed by both subnet-level and NIC-level NSGs.

---

### Why use NIC-level NSG?

To provide VM-specific security controls.

---


# 👨‍💻 Author

## TechWithBSK

Sai Krishna Basam

DevOps & Cloud Engineer

### Skills

* Azure
* AWS
* Kubernetes (AKS)
* Terraform
* Ansible
* Azure DevOps

---

# ⭐ Support

If you found this repository useful:

⭐ Star the repository

🍴 Fork the repository

📺 Subscribe to TechWithBSK

Happy Learning! 🚀
