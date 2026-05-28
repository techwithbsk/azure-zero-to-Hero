# 🌐 Azure Virtual Network & Basic Networking Notes

## 📌 Overview

This repository contains beginner-friendly notes and practical concepts related to:

* Azure Virtual Network (VNet)
* IP Addressing
* Subnetting
* CIDR Notation
* Network ID & Host ID
* Azure Networking Basics

These concepts are essential for:

* Azure Cloud Engineers
* DevOps Engineers
* Kubernetes (AKS)
* Cloud Networking

---

# 🎯 Goals

In Azure Cloud, Microsoft manages the physical network infrastructure, while we are responsible for configuring and managing:

* Virtual Networks (VNets)
* Subnets
* Private Networking
* Public & Private DNS
* Network Security

---

# 🌍 IP Address Basics

An IP Address is a unique address assigned to a device in a network for communication.

## Types of IP Addresses

* IPv4
* IPv6

---

# 🔢 IPv4 Address

IPv4 consists of:

* 32 Bits
* 4 Octets

Example:

192.168.0.10

Binary Representation:

11000000.10101000.00000000.00001010

---

# 🧠 Important Networking Concepts

## Default Gateway

Used to communicate outside the local network.

## Subnet Mask

Used to divide:

* Network ID
* Host ID

---

# 📘 Network ID & Host ID Examples

## Example 1

IP Address:
192.168.0.198

Subnet Mask:
255.255.255.0

Network ID:
192.168.0

Host ID:
198

---

## Example 2

IP Address:
10.0.0.7

Subnet Mask:
255.255.255.0

Network ID:
10.0.0

Host ID:
7

---

# 🌐 Private IP Address Ranges

| Class   | Private Range                 |
| ------- | ----------------------------- |
| Class A | 10.0.0.0 – 10.255.255.255     |
| Class B | 172.16.0.0 – 172.31.255.255   |
| Class C | 192.168.0.0 – 192.168.255.255 |

---

# 📚 Classful Networking

| Class | Default Subnet Mask | Maximum Hosts |
| ----- | ------------------- | ------------- |
| A     | 255.0.0.0           | 16777214      |
| B     | 255.255.0.0         | 65534         |
| C     | 255.255.255.0       | 254           |

---

# 🚀 CIDR (Classless Inter-Domain Routing)

CIDR uses:

* Variable Length Subnet Masks

Notation Example:

192.168.0.0/24

Where:

* `/24` represents subnet mask bits.

Equivalent Subnet Mask:

255.255.255.0

---

# 🧮 CIDR Examples

| CIDR | Subnet Mask   | IP Range                      |
| ---- | ------------- | ----------------------------- |
| /24  | 255.255.255.0 | 192.168.0.0 – 192.168.0.255   |
| /16  | 255.255.0.0   | 192.168.0.0 – 192.168.255.255 |
| /23  | 255.255.254.0 | 192.168.0.0 – 192.168.1.255   |

---

# 🔥 Azure Networking Important Notes

In Azure:

* First IP is reserved for Network ID
* Last IP is reserved for Broadcast

Additionally, Azure reserves:

* x.x.x.1 → Default Gateway
* x.x.x.2 → Azure DNS
* x.x.x.3 → Azure DNS

---

# 📌 Azure Subnet Limitation

Smallest subnet supported in Azure:

/29

---

# 🏗 Azure Virtual Network (VNet)

Azure VNet helps create:

* Secure private networks
* Communication between Azure resources
* Hybrid connectivity
* Internet-facing applications

---

# 🛠 Practical Use Cases

* Hosting Virtual Machines
* AKS Networking
* Secure Application Hosting
* VPN Connectivity
* Hybrid Cloud Architecture

---





# 💡 Technologies Covered

* Azure Virtual Network
* Subnetting
* CIDR
* IP Addressing
* Azure Networking
* Cloud Infrastructure

---

# 👨‍💻 Author

## TechWithBSK

Sai Krishna Basam
DevOps & Cloud Engineer

### Skills:

* Azure
* AWS
* Kubernetes (AKS)
* Terraform
* Ansible
* CI/CD
* DevOps Automation

---

# ⭐ Support

If you found this repository useful:

* ⭐ Star the repository
* 🔁 Share with others
* 📺 Subscribe to TechWithBSK

---
