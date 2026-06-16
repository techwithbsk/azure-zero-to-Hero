# 🌎 Azure Traffic Manager

## 📌 Overview

This project demonstrates how to configure Azure Traffic Manager to distribute user traffic across multiple Azure regions and endpoints.

Azure Traffic Manager is a DNS-based traffic load balancing service that improves application availability, performance, and disaster recovery capabilities.

---

# 🎯 Objectives

* Understand Azure Traffic Manager
* Configure Traffic Manager Profile
* Create Endpoints
* Configure Routing Methods
* Implement Global Traffic Distribution
* Improve Application Availability
* Enable Disaster Recovery

---

# 📚 What is Azure Traffic Manager?

Azure Traffic Manager is a DNS-based traffic routing service.

Instead of routing network traffic directly, Traffic Manager responds to DNS queries and directs users to the most appropriate endpoint.

Benefits:

✅ Global Load Balancing

✅ High Availability

✅ Disaster Recovery

✅ Better User Experience

✅ Multi-Region Deployments

---

# 🏗 Architecture

```text
                     Users
                        │
                        ▼
              Azure Traffic Manager
                        │
         ┌──────────────┴──────────────┐
         ▼                             ▼
      East US                     West Europe
      Web App                     Web App
```

---

# 🔥 How Traffic Manager Works

Step 1:

User requests:

```text
www.techwithbsk.com
```

Step 2:

DNS request reaches:

```text
Azure Traffic Manager
```

Step 3:

Traffic Manager evaluates:

* Endpoint Health
* Routing Method
* User Location

Step 4:

Returns the best endpoint.

---

# ⚠ Prerequisites

Before starting:

* Azure Subscription
* Resource Group
* Two Web Applications or Public Endpoints
* DNS Name

---

# 🛠 Implementation Steps

## Step 1: Create Resource Group

```text
RG-TrafficManager
```

---

## Step 2: Create Web Applications

Example:

```text
WebApp-EastUS

WebApp-WestEurope
```

Deploy sample application to both regions.

---

## Step 3: Create Traffic Manager Profile

Navigate:

```text
Azure Portal
→ Create Resource
→ Traffic Manager Profile
```

Example:

```text
TM-TechWithBSK
```

---

## Step 4: Select Routing Method

Options:

```text
Priority

Performance

Weighted

Geographic

MultiValue

Subnet
```

---

## Step 5: Configure Endpoints

Add:

```text
WebApp-EastUS

WebApp-WestEurope
```

---

## Step 6: Configure Monitoring

Example:

```text
Protocol : HTTPS

Port : 443

Path : /
```

Traffic Manager continuously checks endpoint health.

---

## Step 7: Test Traffic Manager

Access:

```text
https://tm-techwithbsk.trafficmanager.net
```

Verify traffic routing.

---

# 🌎 Routing Methods

## Priority Routing

Used for:

```text
Primary Site
Backup Site
```

Example:

```text
East US → Primary

West Europe → Backup
```

---

## Performance Routing

Routes users to the nearest endpoint.

Example:

```text
India → Southeast Asia

Europe → West Europe
```

---

## Weighted Routing

Distributes traffic based on assigned weights.

Example:

```text
East US → 80%

West Europe → 20%
```

---

## Geographic Routing

Routes users based on geographic location.

Example:

```text
Asia → Asia Endpoint

Europe → Europe Endpoint
```

---

# 🧪 Validation

Verify:

```text
Healthy Endpoint ✔

Nearest Endpoint ✔

Automatic Failover ✔
```

---

# 🚀 Real-World Use Cases

## Global Applications

Serve users from multiple regions.

---

## Disaster Recovery

Automatically redirect traffic during outages.

---

## Blue-Green Deployments

Test new releases with weighted routing.

---

## Regional Compliance

Route users to region-specific applications.

---

# 🔄 Traffic Manager vs Load Balancer

| Feature      | Traffic Manager | Load Balancer   |
| ------------ | --------------- | --------------- |
| Layer        | DNS             | Layer 4         |
| Scope        | Global          | Regional        |
| Routing      | DNS Based       | Network Traffic |
| Multi Region | Yes             | No              |

---

# 🎯 Interview Questions

### What is Azure Traffic Manager?

A DNS-based traffic routing service.

---

### Does Traffic Manager Route Network Traffic?

No.

It routes DNS requests only.

---

### What is the main purpose of Traffic Manager?

Global traffic distribution and high availability.

---

### Which routing method is commonly used for Disaster Recovery?

Priority Routing.

---

### Which routing method routes users to the nearest endpoint?

Performance Routing.

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
