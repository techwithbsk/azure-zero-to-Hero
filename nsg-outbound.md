# 🔒 Azure NSG Outbound Rules

## 📌 Overview

This project demonstrates how to configure Azure Network Security Group (NSG) Outbound Rules to control traffic leaving Azure resources.

Outbound rules help organizations secure workloads by allowing or denying communication to external networks, Azure services, and the internet.

---

# 🎯 Objectives

* Understand NSG Outbound Rules
* Configure Outbound Security Policies
* Allow and Deny Traffic
* Restrict Internet Access
* Secure Azure Workloads
* Validate Network Connectivity

---

# 📚 What are NSG Outbound Rules?

Outbound Rules control traffic leaving Azure resources.

Examples:

✅ VM → Internet

✅ VM → Azure Service

✅ VM → Database

✅ VM → Another Virtual Network

---

# 🏗 Architecture

```text
Virtual Machine
       │
       ▼
Network Security Group
       │
       ▼
Outbound Rule
       │
       ▼
Internet / Azure Services
```

---

# 🔥 Why Use Outbound Rules?

Benefits:

* Control Internet Access
* Improve Security
* Reduce Attack Surface
* Meet Compliance Requirements
* Restrict Unauthorized Communication

---

# ⚠ Prerequisites

Before starting:

* Azure Subscription
* Resource Group
* Virtual Network
* Virtual Machine
* Network Security Group

---

# 🛠 Implementation Steps

## Step 1: Create Resource Group

```text
RG-NSG-OUTBOUND
```

---

## Step 2: Create Virtual Network

```text
10.0.0.0/16
```

---

## Step 3: Create Subnet

```text
10.0.1.0/24
```

---

## Step 4: Create Virtual Machine

Example:

```text
VM-OUTBOUND-DEMO
```

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
NSG-OUTBOUND-DEMO
```

---

## Step 6: Associate NSG

Associate NSG with:

```text
Subnet
or
NIC
```

---

## Step 7: Create Outbound Rule

Navigate:

```text
NSG
→ Outbound Security Rules
→ Add
```

---

### Example Rule 1

Allow HTTPS

```text
Priority    : 100
Destination : Internet
Port        : 443
Protocol    : TCP
Action      : Allow
```

---

### Example Rule 2

Allow HTTP

```text
Priority    : 110
Destination : Internet
Port        : 80
Protocol    : TCP
Action      : Allow
```

---

### Example Rule 3

Deny Internet

```text
Priority    : 200
Destination : Internet
Action      : Deny
```

---

# 📊 Rule Processing

Rules are evaluated by priority.

```text
100 → Allow HTTPS

110 → Allow HTTP

200 → Deny Internet
```

Lower number = Higher priority

---

# 🧪 Connectivity Testing

Verify:

```text
VM → HTTPS Website ✔

VM → HTTP Website ✔

VM → Other Internet Access ✘
```

---

# 🔄 Inbound vs Outbound Rules

| Feature   | Inbound                  | Outbound                 |
| --------- | ------------------------ | ------------------------ |
| Direction | Into VM                  | Out of VM                |
| Purpose   | Protect Incoming Traffic | Control Outgoing Traffic |
| Example   | SSH, RDP                 | Internet Access          |

---

# 🚀 Real-World Use Cases

## Restrict Internet Access

Allow only approved destinations.

---

## Application Security

Allow communication only to required services.

---

## Compliance

Prevent unauthorized data transfer.

---

## Enterprise Security

Control outbound communication from production servers.

---

# 🎯 Interview Questions

### What are Azure NSG Outbound Rules?

Rules that control traffic leaving Azure resources.

---

### Why are Outbound Rules Important?

They prevent unauthorized communication and improve security.

---

### Can NSG Outbound Rules Block Internet Access?

Yes.

Outbound rules can allow or deny internet connectivity.

---

### How are NSG Rules Processed?

Based on Priority.

Lower priority number is evaluated first.

---


# 👨‍💻 Author

## TechWithBSK

Sai Krishna Basam

DevOps & Cloud Engineer

Azure | AWS | Kubernetes | Terraform | Ansible | Azure DevOps

---

# ⭐ Support

If you found this repository useful:

⭐ Star the repository

🍴 Fork the repository

📺 Subscribe to TechWithBSK

Happy Learning! 🚀
