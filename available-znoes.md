# Azure Availability Zone VM Deployment 🚀

## 📌 Project Overview

This project demonstrates how to create and deploy a **Virtual Machine (VM)** inside an **Azure Availability Zone** to achieve high availability and fault tolerance in Microsoft Azure.

The implementation includes:

* Resource Group creation
* Virtual Network (VNet)
* Subnet configuration
* Network Security Group (NSG)
* Azure Virtual Machine deployment
* Availability Zone selection

---

# 🎯 Objectives

* Understand Azure Availability Zones
* Learn High Availability concepts in Azure
* Deploy VM inside a specific Availability Zone
* Configure networking for VM access
* Build foundational Azure Infrastructure

---

# 🏗 Architecture

Azure Region
│
├── Availability Zone 1
│ ├── Virtual Network (VNet)
│ ├── Subnet
│ ├── Network Security Group
│ └── Virtual Machine (VM)
│
├── Availability Zone 2
│
└── Availability Zone 3

---

# 📚 What are Availability Zones?

Availability Zones are physically separate datacenters within an Azure region.

Each zone has:

* Independent power
* Cooling
* Networking

This helps applications remain available even if one datacenter fails.

---

# ✅ Benefits of Availability Zones

* High Availability
* Fault Tolerance
* Better Resilience
* Improved Uptime
* Disaster Recovery Support

---

# 🛠 Services Used

| Service                | Purpose               |
| ---------------------- | --------------------- |
| Resource Group         | Logical container     |
| Virtual Network (VNet) | Private Azure network |
| Subnet                 | Network segmentation  |
| NSG                    | Security rules        |
| Virtual Machine        | Compute resource      |
| Availability Zone      | High availability     |

---

# 🚀 Step-by-Step Implementation

## Step 1: Create Resource Group

* Navigate to Azure Portal
* Create a new Resource Group
* Select Region

---

## Step 2: Create Virtual Network

* Configure VNet Address Space
* Example:

  * 10.0.0.0/16

Create Subnet:

* 10.0.1.0/24

---

## Step 3: Create Network Security Group

Allow:

* RDP (3389) for Windows
  OR
* SSH (22) for Linux

---

## Step 4: Create Virtual Machine

During VM creation:

* Select Availability Zone
* Example:

  * Zone 1

Attach:

* VNet
* Subnet
* NSG

---

# 🔥 Real-Time Use Cases

* Production Applications
* Enterprise Workloads
* Banking Systems
* E-commerce Platforms
* Kubernetes (AKS)
* Disaster Recovery Solutions

---

# 📷 Demo

This project includes:

* Azure Portal VM deployment
* Availability Zone configuration
* Networking setup
* VM connectivity testing

---

# 💡 Key Learnings

* Azure Availability Zones
* High Availability Concepts
* Azure Networking Basics
* VM Deployment
* Infrastructure Design

---

# 🔗 Connect With Me

## TechWithBSK

# ⭐ Support

If you found this project useful:

* Star the repository ⭐
* Share with others 🚀
* Subscribe to TechWithBSK 🎥

---
