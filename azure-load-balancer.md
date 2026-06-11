# ⚖️ Azure Standard Load Balancer

## 📌 Overview

This project demonstrates how to configure Azure Standard Load Balancer to distribute incoming traffic across multiple Virtual Machines and improve application availability.

Azure Standard Load Balancer provides high availability, scalability, and fault tolerance for applications running in Azure.

---

# 🎯 Objectives

* Understand Azure Standard Load Balancer
* Configure Frontend IP
* Create Backend Pool
* Configure Health Probes
* Create Load Balancing Rules
* Test Traffic Distribution
* Build Highly Available Applications

---

# 📚 What is Azure Standard Load Balancer?

Azure Standard Load Balancer distributes incoming network traffic across multiple backend resources.

Benefits:

✅ High Availability

✅ Scalability

✅ Fault Tolerance

✅ Better Performance

✅ Enterprise Ready

---

# 🏗 Architecture

```text
                Internet
                    │
                    ▼
        Azure Standard Load Balancer
                    │
          ┌─────────┴─────────┐
          ▼                   ▼
       VM1                  VM2
    Web Server          Web Server
```

---

# 🔥 Components of Load Balancer

## Frontend IP

Receives incoming client traffic.

Example:

```text
20.x.x.x
```

---

## Backend Pool

Contains backend resources.

Example:

```text
VM1
VM2
```

---

## Health Probe

Monitors backend VM health.

Example:

```text
Protocol : HTTP

Port : 80
```

---

## Load Balancing Rule

Defines how traffic is distributed.

Example:

```text
Frontend Port : 80

Backend Port : 80
```

---

# ⚠ Prerequisites

Before starting:

* Azure Subscription
* Resource Group
* Virtual Network
* Two Virtual Machines
* IIS or Apache Installed

---

# 🛠 Implementation Steps

## Step 1: Create Resource Group

```text
RG-LB-DEMO
```

---

## Step 2: Create Virtual Network

```text
10.0.0.0/16
```

---

## Step 3: Create Two Virtual Machines

Example:

```text
VM1
VM2
```

Install Web Server:

### Linux

```bash
sudo apt update
sudo apt install apache2 -y
```

### Windows

Install IIS.

---

## Step 4: Create Standard Load Balancer

Navigate:

```text
Azure Portal
→ Create Resource
→ Load Balancer
```

Select:

```text
SKU: Standard
Type: Public
```

---

## Step 5: Configure Frontend IP

Create:

```text
Public IP Address
```

Example:

```text
LB-Public-IP
```

---

## Step 6: Create Backend Pool

Add:

```text
VM1
VM2
```

---

## Step 7: Create Health Probe

Configuration:

```text
Protocol : HTTP

Port : 80

Path : /
```

---

## Step 8: Create Load Balancing Rule

```text
Frontend Port : 80

Backend Port : 80

Protocol : TCP
```

---

## Step 9: Configure NSG

Allow:

```text
HTTP (80)

HTTPS (443)
```

---

# 🧪 Validation

Access:

```text
http://LoadBalancer-Public-IP
```

Refresh multiple times.

Expected:

```text
Requests distributed between VM1 and VM2
```

---

# 🚀 Real-World Use Cases

## Web Applications

Distribute traffic across multiple web servers.

---

## Enterprise Applications

Improve application availability.

---

## APIs

Handle large numbers of requests.

---

## High Availability Solutions

Prevent single points of failure.

---

# 🎯 Interview Questions

### What is Azure Standard Load Balancer?

A Layer 4 load balancing service that distributes network traffic across backend resources.

---

### What is a Backend Pool?

A collection of VMs or resources that receive traffic from the Load Balancer.

---

### What is a Health Probe?

A mechanism used to determine backend resource health.

---

### What happens if VM1 fails?

Traffic is automatically routed to healthy backend VMs.

---

### What Layer Does Azure Load Balancer Operate On?

Layer 4 (TCP/UDP).

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
