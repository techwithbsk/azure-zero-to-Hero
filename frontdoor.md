# 🚪 Azure Front Door

## 📌 Overview

Azure Front Door is Microsoft's global application delivery network (ADN) that provides high availability, intelligent routing, acceleration, and security for web applications.

It operates at Layer 7 (HTTP/HTTPS) and routes users to the nearest healthy backend using Microsoft's global edge network.

---

# 🎯 Objectives

* Understand Azure Front Door
* Configure Front Door Profile
* Configure Backend Pools
* Configure Routing Rules
* Enable WAF Protection
* Implement Global Load Balancing
* Build Highly Available Applications

---

# 📚 What is Azure Front Door?

Azure Front Door is a global Layer 7 load balancing and application acceleration service.

Key Features:

✅ Global Load Balancing

✅ Layer 7 Routing

✅ SSL/TLS Offloading

✅ Web Application Firewall (WAF)

✅ URL-Based Routing

✅ Multi-Region Failover

---

# 🏗 Architecture

```text
                   Global Users
                        │
                        ▼
                Azure Front Door
                        │
          ┌─────────────┴─────────────┐
          ▼                           ▼
      East US                    West Europe
      Web App                     Web App
```

---

# 🔥 How Azure Front Door Works

Step 1:

User accesses:

```text
www.techwithbsk.com
```

Step 2:

Request reaches:

```text
Azure Front Door Edge Location
```

Step 3:

Front Door evaluates:

* Backend Health
* Latency
* Routing Rules
* WAF Policies

Step 4:

Routes traffic to the best backend.

---

# ⚠ Prerequisites

Before starting:

* Azure Subscription
* Resource Group
* Two Web Applications
* Public Endpoints

---

# 🛠 Implementation Steps

## Step 1: Create Resource Group

```text
RG-FrontDoor-Demo
```

---

## Step 2: Deploy Web Applications

Example:

```text
WebApp-EastUS

WebApp-WestEurope
```

---

## Step 3: Create Azure Front Door

Navigate:

```text
Azure Portal
→ Create Resource
→ Front Door and CDN Profiles
```

Example:

```text
FD-TechWithBSK
```

---

## Step 4: Create Frontend Endpoint

Example:

```text
techwithbsk.azurefd.net
```

---

## Step 5: Configure Backend Pool

Add:

```text
WebApp-EastUS

WebApp-WestEurope
```

---

## Step 6: Configure Health Probes

Example:

```text
Protocol : HTTPS

Path : /
```

Front Door continuously checks backend health.

---

## Step 7: Configure Routing Rule

```text
Frontend Endpoint
        │
        ▼
Backend Pool
```

---

## Step 8: Test Application

Access:

```text
https://techwithbsk.azurefd.net
```

Verify traffic routing.

---

# 🔒 Web Application Firewall (WAF)

Azure Front Door integrates with WAF.

Benefits:

✅ SQL Injection Protection

✅ Cross-Site Scripting Protection

✅ OWASP Rules

✅ DDoS Mitigation Support

---

# 🚀 Real-World Use Cases

## Global Applications

Serve users worldwide with low latency.

---

## Disaster Recovery

Automatically redirect traffic to healthy regions.

---

## Multi-Region Deployments

Improve application availability.

---

## Secure Internet Applications

Protect applications using WAF.

---

# 🔄 Front Door vs Traffic Manager

| Feature        | Front Door | Traffic Manager   |
| -------------- | ---------- | ----------------- |
| Layer          | Layer 7    | DNS Based         |
| Routing        | HTTP/HTTPS | DNS               |
| Failover       | Fast       | DNS TTL Dependent |
| WAF            | Yes        | No                |
| SSL Offloading | Yes        | No                |

---

# 🔄 Front Door vs Application Gateway

| Feature      | Front Door | Application Gateway |
| ------------ | ---------- | ------------------- |
| Scope        | Global     | Regional            |
| Layer        | Layer 7    | Layer 7             |
| WAF          | Yes        | Yes                 |
| Multi Region | Yes        | No                  |

---

# 🎯 Interview Questions

### What is Azure Front Door?

A global Layer 7 application delivery and load balancing service.

---

### Does Azure Front Door support WAF?

Yes.

Front Door integrates with Azure Web Application Firewall.

---

### What is the difference between Front Door and Traffic Manager?

Traffic Manager is DNS-based.

Front Door routes actual HTTP/HTTPS traffic.

---

### What layer does Azure Front Door operate on?

Layer 7 (Application Layer).

---

### Can Azure Front Door be used for Disaster Recovery?

Yes.

It automatically routes traffic to healthy backends.

---

# 👨‍💻 Author

TechWithBSK

Sai Krishna Basam

DevOps & Cloud Engineer

Azure | AWS | Kubernetes | Terraform | Ansible | Azure DevOps

---

# ⭐ Support

⭐ Star this repository

🍴 Fork the repository

📺 Subscribe to TechWithBSK

Happy Learning! 🚀
