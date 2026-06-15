# 🚪 Azure Application Gateway

## 📌 Overview

This project demonstrates how to configure Azure Application Gateway to securely distribute web traffic across backend web servers.

Azure Application Gateway is a Layer 7 load balancer that provides advanced traffic management features such as URL-based routing, SSL termination, and Web Application Firewall (WAF).

---

# 🎯 Objectives

* Understand Azure Application Gateway
* Configure Frontend IP
* Create Backend Pools
* Configure Listeners
* Create Routing Rules
* Enable SSL Termination
* Understand WAF Integration

---

# 📚 What is Azure Application Gateway?

Azure Application Gateway is a web traffic load balancer that operates at Layer 7 (Application Layer).

Features:

✅ URL-Based Routing

✅ SSL/TLS Termination

✅ Cookie-Based Session Affinity

✅ Web Application Firewall (WAF)

✅ Multi-Site Hosting

✅ End-to-End SSL

---

# 🏗 Architecture

```text
                    Internet
                        │
                        ▼
              Azure Application Gateway
                        │
              ┌─────────┴─────────┐
              ▼                   ▼
          Web Server 1       Web Server 2
```

---

# 🔥 Application Gateway Components

## Frontend IP

Receives client traffic.

Example:

```text
Public IP Address
```

---

## Backend Pool

Contains backend resources.

Example:

```text
WebVM1
WebVM2
```

---

## Listener

Listens for incoming requests.

Example:

```text
HTTP : 80

HTTPS : 443
```

---

## HTTP Settings

Defines backend communication settings.

Example:

```text
Port : 80
Protocol : HTTP
```

---

## Routing Rule

Maps requests to backend resources.

Example:

```text
Listener → Backend Pool
```

---

# ⚠ Prerequisites

Before starting:

* Azure Subscription
* Resource Group
* Virtual Network
* Subnet for Application Gateway
* Two Virtual Machines

---

# 🛠 Implementation Steps

## Step 1: Create Resource Group

```text
RG-AppGateway-Demo
```

---

## Step 2: Create Virtual Network

```text
10.0.0.0/16
```

Create Subnets:

```text
AppGateway-Subnet

Web-Subnet
```

⚠ Application Gateway requires a dedicated subnet.

---

## Step 3: Create Virtual Machines

Example:

```text
WebVM1

WebVM2
```

Install web server:

### Ubuntu

```bash
sudo apt update
sudo apt install nginx -y
```

---

## Step 4: Create Application Gateway

Navigate:

```text
Azure Portal
→ Create Resource
→ Application Gateway
```

Choose:

```text
Standard V2
```

or

```text
WAF V2
```

---

## Step 5: Configure Frontend IP

Create:

```text
Public IP Address
```

Example:

```text
AppGateway-PIP
```

---

## Step 6: Configure Backend Pool

Add:

```text
WebVM1

WebVM2
```

---

## Step 7: Configure Listener

Example:

```text
HTTP Listener
Port : 80
```

---

## Step 8: Configure HTTP Settings

```text
Protocol : HTTP

Port : 80
```

---

## Step 9: Create Routing Rule

```text
Listener
      │
      ▼
Backend Pool
```

---

## Step 10: Test Application

Access:

```text
http://ApplicationGateway-IP
```

Expected:

```text
Traffic routed to backend servers
```

---

# 🔒 Web Application Firewall (WAF)

Application Gateway supports WAF.

Benefits:

✅ Protect Against SQL Injection

✅ Protect Against Cross-Site Scripting (XSS)

✅ OWASP Security Rules

✅ Enhanced Application Security

---

# 🧪 Validation

Verify:

```text
Internet
     │
     ▼
Application Gateway
     │
     ▼
Backend VMs
```

Traffic successfully reaches backend resources.

---

# 🚀 Real-World Use Cases

## Multi-Site Hosting

Host multiple websites using one gateway.

---

## URL-Based Routing

Example:

```text
/app → App Server

/api → API Server
```

---

## SSL Offloading

Reduce backend server workload.

---

## WAF Protection

Protect public-facing applications.

---

# 🎯 Interview Questions

### What is Azure Application Gateway?

A Layer 7 load balancer used for web traffic management.

---

### Which Layer Does Application Gateway Operate On?

Layer 7 (Application Layer).

---

### What is the difference between Load Balancer and Application Gateway?

Load Balancer:

```text
Layer 4
TCP/UDP
```

Application Gateway:

```text
Layer 7
HTTP/HTTPS
```

---

### Why Use Application Gateway?

For advanced web traffic routing and security.

---

### What is WAF?

Web Application Firewall used to protect web applications from common attacks.

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
