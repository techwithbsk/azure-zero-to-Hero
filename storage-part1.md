# Azure Storage Account - Part 1

# Blob Storage & Static Website Hosting

## Overview

This project demonstrates the basics of Azure Storage Account with a focus on **Blob Storage** and **Static Website Hosting**.

Blob Storage is used to store unstructured data such as images, videos, documents, backups, and application assets.

Azure Storage also allows hosting static websites without deploying a web server.

---

# Objectives

* Create Azure Storage Account
* Understand Blob Storage
* Create Blob Containers
* Upload Files
* Configure Access Levels
* Enable Static Website
* Host HTML Website

---

# Architecture

```text
Users
      │
      ▼
Azure Storage Account
      │
 ┌────┴─────────┐
 ▼              ▼
Blob Storage   Static Website
```

---

# What is Blob Storage?

Blob Storage is Microsoft's object storage service.

It stores:

* Images
* Videos
* Documents
* Backups
* Logs
* Application Files

---

# Blob Types

## Block Blob

Used for:

* Images
* Videos
* Documents
* Backups

---

## Append Blob

Used for:

* Logs
* Monitoring
* Audit Files

---

## Page Blob

Used for:

* Azure Managed Disks
* Virtual Machine VHD Files

---

# Storage Account

Navigate:

Azure Portal

→ Storage Accounts

→ Create

Configuration:

* Subscription
* Resource Group
* Storage Account Name
* Region
* Standard Performance
* LRS Redundancy

---

# Create Blob Container

Navigate:

Storage Account

↓

Containers

↓

Create Container

Example:

```text
images
```

---

# Access Levels

## Private

Only authenticated users.

---

## Blob

Anonymous read access for blobs only.

---

## Container

Anonymous read access for entire container.

---

# Upload Files

Upload:

* Images
* HTML
* CSS
* JavaScript

Verify successful upload.

---

# Static Website Hosting

Navigate:

Storage Account

↓

Data Management

↓

Static Website

↓

Enable

---

Azure Creates

```text
$web
```

container automatically.

---

# Upload Website Files

Upload:

```text
index.html

style.css

script.js
```

---

# Browse Website

Azure generates:

```text
https://<storage-account>.zXX.web.core.windows.net
```

Open URL in browser.

---

# Real-World Use Cases

## Blob Storage

* Images
* Videos
* Backup Files
* Documents
* Application Assets

---

## Static Website

* Portfolio Website
* Company Landing Page
* Documentation Site
* Resume Website

---

# Security Best Practices

* Use Private Access by default
* Enable HTTPS Only
* Use Shared Access Signatures (SAS)
* Enable Soft Delete
* Enable Versioning

---

# Interview Questions

## What is Azure Blob Storage?

Object storage for unstructured data.

---

## What are the Blob Types?

* Block Blob
* Append Blob
* Page Blob

---

## Which Blob is used for Azure VM Disks?

Page Blob.

---

## Which Blob is used for Images and Videos?

Block Blob.

---

## What is the $web Container?

A special container automatically created when Static Website Hosting is enabled.

---

## Can Azure Storage host websites?

Yes.

It can host HTML, CSS, JavaScript, and other static content without a web server.

---

# Next Video

Azure Storage Account Part 2

* Azure File Share
* Queue Storage
* Table Storage
* Storage Explorer
* Shared Access Signature (SAS)

---

# Author

**TechWithBSK**

Sai Krishna Basam

Azure | AWS | Kubernetes | Terraform | Azure DevOps

Happy Learning! 🚀
