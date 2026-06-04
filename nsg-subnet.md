# 🔒 Azure NSG at Subnet Level

## 📌 Overview

This project demonstrates how to configure Azure Network Security Groups (NSGs) at the Subnet Level to secure Azure resources and control inbound and outbound network traffic.

Subnet-level NSGs apply security rules to all resources within a subnet, making them ideal for centralized network security management.

---

# 🎯 Objectives

* Understand Azure NSG
* Configure NSG at Subnet Level
* Create Inbound Rules
* Create Outbound Rules
* Secure Azure Resources
* Test Network Connectivity

---

# 🏗 Architecture

```text
Internet
    │
    ▼
Virtual Network
    │
    ▼
Subnet
    │
    ▼
Network Security Group
    │
    ▼
Virtual Machines
```

---

# 📚 What is Azure NSG?

Azure Network Security Group (NSG) is a network security service that controls traffic entering and leaving Azure resources.

NSGs allow:

✅ Allow Traffic

✅ Deny Traffic

✅ Inbound Rules

✅ Outbound Rules

✅ Traffic Filtering

---

# 🔥 Why Use NSG at Subnet Level?

Benefits:

* Centralized Security Management
* Consistent Security Rules
* Easy Administration
* Improved Compliance
* Reduced Configuration Effort

---

# ⚠ Prerequisites

Before starting:

* Azure Subscription
* Resource Group
* Virtual Network
* Subnet
* Virtual Machine

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
```

---

## Step 3: Create Subnet

```text
Subnet: 10.0.1.0/24
```

---

## Step 4: Create Virtual Machines

Example:

```text
VM1
VM2
```

Deploy both VMs into the same subnet.

---

## Step 5: Create Network Security Group

Navigate:

```text
Azure Portal
→ Create Resource
→ Network Security Group
```

Example:

```text
NSG-Subnet-Demo
```

---

## Step 6: Associate NSG with Subnet

Navigate:

```text
Virtual Network
→ Subnets
→ Select Subnet
→ Associate NSG
```

Select:

```text
NSG-Subnet-Demo
```

---

# 🔒 Example Inbound Rules

Allow SSH

```text
Priority : 100
Port     : 22
Action   : Allow
```

---

Allow RDP

```text
Priority : 110
Port     : 3389
Action   : Allow
```

---

Allow HTTP

```text
Priority : 120
Port     : 80
Action   : Allow
```

---

Allow HTTPS

```text
Priority : 130
Port     : 443
Action   : Allow
```

---

# 🔒 Example Outbound Rules

Allow Internet Access

```text
Destination : Internet
Action      : Allow
```

---

# 📊 Rule Processing

Rules are processed based on priority.

```text
100 → Allow SSH
110 → Allow RDP
120 → Allow HTTP
130 → Allow HTTPS
200 → Deny All
```

Lower number = Higher priority

---

# 🧪 Connectivity Testing

Verify:

```text
Internet → VM ✔
Allowed Ports ✔
Blocked Ports ✘
```

---

# 🔄 Subnet-Level vs NIC-Level NSG

| Feature    | Subnet Level       | NIC Level         |
| ---------- | ------------------ | ----------------- |
| Scope      | Entire Subnet      | Single VM         |
| Management | Centralized        | Granular          |
| Use Case   | Multiple Resources | Specific Resource |

---

# 🚀 Real-World Use Cases

* Web Server Security
* Application Security
* Database Protection
* Shared Services Networks
* Enterprise Azure Environments

---

# 🎯 Interview Questions

### What is Azure NSG?

A security service used to control inbound and outbound network traffic.

---

### What is Subnet-Level NSG?

An NSG associated with a subnet that applies rules to all resources within that subnet.

---

### Can NSG be applied at both Subnet and NIC level?

Yes.

Azure supports:

* Subnet-Level NSG
* NIC-Level NSG

---

### Which rule is processed first?

The rule with the lowest priority number.

---


# 👨‍💻 Author

## TechWithBSK

Sai Krishna Basam

DevOps & Cloud Engineer

### Technologies

* Azure
* AWS
* Kubernetes
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
