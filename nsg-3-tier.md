# 🔒 Azure NSG in Three-Tier Architecture

## 📌 Overview

This project demonstrates how to secure a Three-Tier Application Architecture in Azure using Network Security Groups (NSGs).

The architecture consists of:

* Web Tier
* Application Tier
* Database Tier

Each tier is protected using dedicated NSGs to ensure secure communication and network isolation.

---

# 🎯 Objectives

* Understand Three-Tier Architecture
* Implement Azure NSGs
* Secure Web, App, and Database Layers
* Control East-West Traffic
* Apply Least Privilege Security
* Validate Connectivity Between Tiers

---

# 🏗 Architecture

```text
                Internet
                    │
                    ▼
            Web Tier Subnet
              (Frontend VM)
                    │
                    ▼
         Application Tier Subnet
             (Application VM)
                    │
                    ▼
          Database Tier Subnet
             (Database VM)
```

---

# 📚 Three-Tier Architecture

## Web Tier

Responsibilities:

* Accept user requests
* Host web applications
* Public-facing layer

Example:

* Nginx
* Apache
* IIS

---

## Application Tier

Responsibilities:

* Business Logic
* API Processing
* Application Services
Ex:

* Tomcat
---

## Database Tier

Responsibilities:

* Data Storage
* Database Processing

Example:

* SQL Server
* MySQL
* PostgreSQL

---

# 🔒 NSG Design

## Web Tier NSG

Allow:

```text
HTTP  (80)
HTTPS (443)
```

Source:

```text
Internet
```

---

## Application Tier NSG

Allow:

```text
Port 8080
```

Source:

```text
Web Tier Subnet
```

Deny:

```text
Internet Access
```

---

## Database Tier NSG

Allow:

```text
MySQL Port 3306
```

Source:

```text
Application Tier Subnet
```

Deny:

```text
Web Tier Access
Internet Access
```

---

# ⚠ Security Principle

Only allow required traffic.

Everything else should be denied.

This follows:

* Zero Trust
* Least Privilege Access
* Defense in Depth

---

# 🛠 Implementation Steps

## Step 1

Create Resource Group

```text
RG-ThreeTier
```

---

## Step 2

Create Virtual Network

```text
10.1.0.0/16
```

---

## Step 3

Create Subnets

```text
Web-Subnet
10.1.0.0/24

App-Subnet
10.1.1.0/24

DB-Subnet
10.1.2.0/24
```

---

## Step 4

Deploy Virtual Machines

```text
WebVM
AppVM
DBVM
```

---

## Step 5

Create NSGs

```text
NSG-Web
NSG-App
NSG-DB
```

---

## Step 6

Associate NSGs

```text
NSG-Web → Web Subnet

NSG-App → App Subnet

NSG-DB → DB Subnet
```

---

## Step 7

Create Security Rules

Configure:

* HTTP
* HTTPS
* Application Ports
* Database Ports

Based on tier requirements.

---

# 🧪 Connectivity Validation

Verify:

```text
Internet → WebVM ✔

WebVM → AppVM ✔

AppVM → DBVM ✔

Internet → DBVM ✘

Internet → AppVM ✘
```

---

# 🚀 Benefits

* Enhanced Security
* Network Segmentation
* Reduced Attack Surface
* Better Compliance
* Enterprise Architecture Pattern

---

# 🎯 Interview Questions

### What is Three-Tier Architecture?

An architecture that separates Presentation, Business Logic, and Database layers.

---

### Why use NSGs?

To control inbound and outbound traffic.

---

### Why isolate Database Tier?

To prevent direct access from Internet and improve security.

---

### Which traffic should Database Tier allow?

Only traffic from Application Tier.

---


# 👨‍💻 Author

## TechWithBSK

Sai Krishna Basam

DevOps & Cloud Engineer

### Skills

* Azure
* AWS
* Kubernetes
* Terraform
* Ansible
* Azure DevOps

---

# ⭐ Support

If you found this project useful:

⭐ Star the repository

🍴 Fork the repository

📺 Subscribe to TechWithBSK

Happy Learning! 🚀
