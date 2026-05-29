# 🌐 Azure Virtual Network (VNet) Peering

## 📌 Overview

This project demonstrates how to configure Azure Virtual Network (VNet) Peering to enable secure and private communication between Azure Virtual Networks.

VNet Peering allows Azure resources in different virtual networks to communicate using Microsoft's private backbone network without requiring VPNs or public internet access.

---

# 🎯 Objectives

* Understand Azure VNet Peering
* Connect VNets within the same subscription
* Connect VNets across different subscriptions
* Enable private communication between Azure resources
* Verify connectivity between virtual machines
* Understand real-world Azure networking scenarios

---

# 🏗 Architecture

```text
Subscription A

VNet-1
10.0.0.0/16
    │
    │
VNet Peering
    │
    │
VNet-2
10.1.0.0/16

Subscription B
```

After peering is established:

* Resources communicate using Private IP Addresses
* Traffic stays on Microsoft's Backbone Network
* No VPN Gateway required
* High bandwidth and low latency connectivity

---

# 📚 What is Azure VNet Peering?

Azure VNet Peering enables seamless connectivity between two Azure Virtual Networks.

It provides:

✅ Private Communication

✅ High Performance

✅ Low Latency

✅ No Internet Exposure

✅ Easy Configuration

✅ Secure Connectivity

---

# 🔥 Types of VNet Peering

## 1. Regional VNet Peering

Connect VNets located within the same Azure Region.

### Example

```text
East US

VNet-1 ↔ VNet-2
```

Benefits:

* Low latency
* High throughput
* Private connectivity

---

## 2. Global VNet Peering

Connect VNets located in different Azure Regions.

### Example

```text
East US
   ↕
Global VNet Peering
   ↕
West Europe
```

Benefits:

* Cross-region communication
* Global application deployments
* Disaster recovery solutions

---

# 🌍 Cross-Subscription VNet Peering

Azure supports VNet Peering between:

✅ Same Resource Group

✅ Different Resource Groups

✅ Same Subscription

✅ Different Subscriptions

✅ Same Azure Region

✅ Different Azure Regions

### Example

```text
Subscription-A

VNet-1
10.0.0.0/16

      ↕
  VNet Peering
      ↕

Subscription-B

VNet-2
10.1.0.0/16
```

Requirements:

* Appropriate RBAC permissions
* Access to both subscriptions
* Non-overlapping address spaces

---

# ⚠ Prerequisites

Before configuring VNet Peering:

* Azure Subscription
* Resource Groups
* Two Virtual Networks
* Non-overlapping Address Spaces
* Virtual Machines (Optional for Testing)

---

# 🛠 Implementation Steps

## Step 1: Create Resource Groups

Create:

```text
RG-VNET1
RG-VNET2
```

---

## Step 2: Create Virtual Networks

### VNet-1

```text
Address Space: 10.0.0.0/16
Subnet: 10.0.1.0/24
```

### VNet-2

```text
Address Space: 10.1.0.0/16
Subnet: 10.1.1.0/24
```

---

## Step 3: Create Virtual Machines

Deploy:

```text
VM1 → VNet-1
VM2 → VNet-2
```

Purpose:

* Connectivity validation
* Real-world testing

---

## Step 4: Configure VNet Peering

Navigate to:

```text
Virtual Network
→ Peerings
→ Add
```

Configure:

### VNet-1 → VNet-2

Enable:

```text
Allow Virtual Network Access
```

### VNet-2 → VNet-1

Enable:

```text
Allow Virtual Network Access
```

Save the configuration.

---

## Step 5: Validate Connectivity

Connect to VM1 and test VM2.

### Windows

```powershell
ping <Private-IP-of-VM2>
```

### Linux

```bash
ping <Private-IP-of-VM2>
```

Repeat from VM2 to VM1.

Expected Result:

```text
Successful communication using Private IPs
```

---

# 🚀 Benefits of VNet Peering

* Low Latency Communication
* High Network Throughput
* No VPN Required
* Secure Private Connectivity
* Simplified Network Design
* Cost Effective

---

# 🌍 Real-World Use Cases

* Application-to-Database Communication
* Development and Production Connectivity
* Shared Services Access
* Cross-Subscription Networking
* Enterprise Cloud Deployments
* Multi-Team Azure Environments
* Centralized Monitoring Solutions
* Logging and Security Platforms

---

# 🎯 Interview Questions

### What is Azure VNet Peering?

Azure VNet Peering connects two Azure Virtual Networks using Microsoft's private backbone network.

---

### Can Azure VNet Peering work across subscriptions?

Yes. Azure supports VNet Peering across different subscriptions with appropriate permissions.

---

### Can Azure VNet Peering work across regions?

Yes. This is called Global VNet Peering.

---

### What is the primary requirement for VNet Peering?

The VNets must have non-overlapping IP address spaces.

---



# 👨‍💻 Author

## TechWithBSK

Sai Krishna Basam

DevOps & Cloud Engineer | Azure | AWS | Kubernetes | Terraform | Ansible | CI/CD


# ⭐ Support

If you found this repository useful:

⭐ Star the repository

🍴 Fork the repository

📺 Subscribe to TechWithBSK

Happy Learning! 🚀
