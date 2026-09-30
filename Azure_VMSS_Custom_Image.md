# Azure VM Scale Sets Using a Custom VM Image

## Custom Image + VMSS \| Azure Zero to Hero

### Overview

This hands-on lab demonstrates how to use an **Azure Custom VM Image**
with **Virtual Machine Scale Sets (VMSS)**.

The custom image contains the operating system, applications, packages,
configuration, and other required software. The VM Scale Set then uses
this image as the base for creating multiple identical VM instances.

This approach is useful when you want **consistent, repeatable, and
scalable VM deployments**.

------------------------------------------------------------------------

## Architecture

``` text
                         Internet
                            |
                            v
                   Azure Load Balancer
                            |
                            v
                 Virtual Machine Scale Set
                            |
          +-----------------+-----------------+
          |                 |                 |
          v                 v                 v
       VMSS VM 1          VMSS VM 2          VMSS VM 3
          |                 |                 |
          +-----------------+-----------------+
                            |
                     Same Custom Image
                            |
                            v
                 Azure Compute Gallery
                            |
                            v
                 Custom VM Image Version
```

------------------------------------------------------------------------

# Objectives

In this lab, you will learn how to:

-   Create and prepare an Azure Virtual Machine.
-   Install required applications and configurations.
-   Create a reusable Custom VM Image.
-   Store and manage the image using Azure Compute Gallery.
-   Create a VM Scale Set using the Custom Image.
-   Configure VMSS instance count.
-   Configure Azure Load Balancer.
-   Scale VMSS manually.
-   Configure autoscaling.
-   Verify that all VMSS instances use the same custom image.
-   Understand the real-world use of Golden Images with VMSS.

------------------------------------------------------------------------

# Prerequisites

-   Azure Subscription
-   Azure Portal access
-   Existing Azure Virtual Machine
-   Virtual Network
-   Basic knowledge of Azure VM
-   Basic knowledge of VM Scale Sets

------------------------------------------------------------------------

# Example Resources

  Resource                Example Name
  ----------------------- ---------------------
  Resource Group          RG-VMSS-CustomImage
  Source VM               VM-GoldenImage
  Azure Compute Gallery   gallery-techwithbsk
  Image Definition        ubuntu-web
  Image Version           1.0.0
  VM Scale Set            vmss-web
  Virtual Network         vnet-vmss
  Subnet                  subnet-web
  Load Balancer           lb-vmss

------------------------------------------------------------------------

# Part 1 - Prepare the Source VM

The first step is to create a VM that will become the source for the
custom image.

Example:

``` text
VM-GoldenImage
```

The source VM should contain all the software and configuration required
by the VMSS instances.

------------------------------------------------------------------------

## Install Required Applications

For an Ubuntu-based web server:

``` bash
sudo apt update
sudo apt upgrade -y
```

Install Nginx:

``` bash
sudo apt install nginx -y
```

Verify:

``` bash
sudo systemctl status nginx
```

Test locally:

``` bash
curl localhost
```

------------------------------------------------------------------------

# Part 2 - Customize the VM

Install and configure all required components before creating the image.

Examples:

``` text
Nginx
Docker
Java
Azure CLI
Monitoring Agents
Application Packages
Configuration Files
Security Packages
```

Example:

``` bash
sudo apt install docker.io -y
```

Verify:

``` bash
docker --version
```

------------------------------------------------------------------------

# Part 3 - Prepare the VM for Imaging

Before capturing a Linux VM image, deprovision the VM so that
machine-specific information is removed.

Example:

``` bash
sudo waagent -deprovision+user
```

Then shut down the VM.

``` bash
sudo shutdown now
```

> Follow the Azure-supported image preparation process for the operating
> system you are using.

------------------------------------------------------------------------

# Part 4 - Create Azure Compute Gallery

Navigate to:

``` text
Azure Portal
    |
Azure Compute Galleries
    |
Create
```

Example:

``` text
Gallery Name:
gallery-techwithbsk
```

Azure Compute Gallery provides a centralized way to manage custom VM
images and image versions.

------------------------------------------------------------------------

# Part 5 - Create Image Definition

Inside the gallery, create an image definition.

Example:

``` text
Image Definition:
ubuntu-web
```

Example configuration:

``` text
Operating System:
Linux

OS State:
Generalized

Publisher:
TechWithBSK

Offer:
Ubuntu-Web

SKU:
1.0
```

------------------------------------------------------------------------

# Part 6 - Create Image Version

Create an image version from the source VM.

Example:

``` text
Image Version:
1.0.0
```

Architecture:

``` text
Source VM
    |
    v
Generalize VM
    |
    v
Azure Compute Gallery
    |
    v
Image Definition
    |
    v
Image Version 1.0.0
```

------------------------------------------------------------------------

# Part 7 - Verify Custom Image

After the image version is created, verify that the image is available.

Navigate to:

``` text
Azure Compute Gallery
    |
gallery-techwithbsk
    |
ubuntu-web
    |
Versions
```

Example:

``` text
1.0.0
```

------------------------------------------------------------------------

# Part 8 - Create VM Scale Set Using Custom Image

Navigate to:

``` text
Azure Portal
    |
Virtual Machine Scale Sets
    |
Create
```

Select:

``` text
Resource Group:
RG-VMSS-CustomImage

VMSS Name:
vmss-web

Region:
Your Azure Region
```

------------------------------------------------------------------------

## Select Custom Image

Under the image selection, choose your Azure Compute Gallery image.

Example:

``` text
Azure Compute Gallery
    |
gallery-techwithbsk
    |
ubuntu-web
    |
1.0.0
```

The VMSS will use this image as the base image for its instances.

------------------------------------------------------------------------

# Part 9 - Configure VMSS Instances

Example:

``` text
Initial Instance Count = 2
Minimum Instances = 2
Maximum Instances = 5
```

The VMSS creates:

``` text
Custom Image
     |
     +---- VMSS Instance 1
     |
     +---- VMSS Instance 2
```

Both instances are created from the same custom image.

------------------------------------------------------------------------

# Part 10 - Configure Networking

Select:

``` text
Virtual Network:
vnet-vmss

Subnet:
subnet-web
```

Configure a Load Balancer if the application needs incoming traffic
distribution.

Architecture:

``` text
Internet
    |
    v
Azure Load Balancer
    |
    +------------------+
    |                  |
    v                  v
VMSS Instance 1    VMSS Instance 2
```

------------------------------------------------------------------------

# Part 11 - Verify Application

If Nginx was installed in the custom image, the VMSS instances should
already contain Nginx.

Verify on an instance:

``` bash
sudo systemctl status nginx
```

Test:

``` bash
curl localhost
```

This demonstrates the benefit of using a custom image: required software
is already present when new VMSS instances are created.

------------------------------------------------------------------------

# Part 12 - Verify VMSS Instances

Navigate to:

``` text
VM Scale Set
    |
Instances
```

Example:

``` text
Instance 0
Instance 1
```

Scale the VMSS to four instances:

``` text
Instance 0
Instance 1
Instance 2
Instance 3
```

The newly created instances are also based on the selected custom image
version.

------------------------------------------------------------------------

# Part 13 - Manual Scaling

Navigate to:

``` text
VM Scale Set
    |
Scaling
```

Increase the instance count:

``` text
2 --> 4
```

VMSS creates additional instances using the configured custom image.

Architecture:

``` text
Custom Image
     |
     +---- VM 1
     +---- VM 2
     +---- VM 3
     +---- VM 4
```

------------------------------------------------------------------------

# Part 14 - Configure Autoscaling

Configure autoscaling based on a metric such as CPU utilization.

Example:

``` text
Minimum Instances = 2
Default Instances = 2
Maximum Instances = 5
```

Scale-out rule:

``` text
CPU > 70%
    |
    v
Add VM Instance
```

Scale-in rule:

``` text
CPU < 30%
    |
    v
Remove VM Instance
```

------------------------------------------------------------------------

# Part 15 - Test Custom Image + VMSS

Increase the VMSS instance count and verify that the new instances
contain the software from the custom image.

For example:

``` bash
nginx -v
```

and:

``` bash
sudo systemctl status nginx
```

You can also verify the application:

``` bash
curl localhost
```

------------------------------------------------------------------------

# End-to-End Flow

``` text
Create Source VM
       |
       v
Install Applications
       |
       v
Configure VM
       |
       v
Generalize VM
       |
       v
Create Custom Image
       |
       v
Azure Compute Gallery
       |
       v
Create Image Version
       |
       v
Create VM Scale Set
       |
       v
Select Custom Image
       |
       v
Create VMSS Instances
       |
       v
Azure Load Balancer
       |
       v
Autoscaling
```

------------------------------------------------------------------------

# Why Use Custom Images with VMSS?

A custom image allows you to prepare a standard VM once and reuse it
across multiple VMSS instances.

Without a custom image:

``` text
Create VM
    |
Install Software
    |
Configure Software
    |
Patch VM
    |
Repeat for every VM
```

With a custom image:

``` text
Create & Configure Once
          |
          v
      Custom Image
          |
    +-----+-----+
    |     |     |
   VM1   VM2   VM3
```

------------------------------------------------------------------------

# Real-World Use Cases

## Web Applications

Create a standard web-server image containing:

``` text
Ubuntu
Nginx
Application Code
Monitoring Agent
Security Configuration
```

Use the image with VMSS to deploy multiple web servers.

------------------------------------------------------------------------

## Application Servers

Create a custom image containing:

``` text
Operating System
Java
Application Runtime
Monitoring Agent
Security Tools
```

VMSS can then create multiple application server instances.

------------------------------------------------------------------------

## Golden Images

Organizations can maintain standardized images containing:

-   OS configuration
-   Security patches
-   Required software
-   Monitoring agents
-   Company configuration
-   Application dependencies

------------------------------------------------------------------------

# Custom Image + VMSS Benefits

  Feature             Benefit
  ------------------- ------------------------------------------------
  Consistency         Every VMSS instance starts from the same image
  Faster Deployment   Applications are pre-installed
  Scalability         New instances can be created quickly
  Standardization     Common OS and application configuration
  Automation          Works well with CI/CD
  Versioning          Image versions can be maintained
  High Availability   Multiple VMSS instances can run simultaneously

------------------------------------------------------------------------

# Custom Image vs Marketplace Image

  -----------------------------------------------------------------------
  Feature                 Marketplace Image       Custom Image
  ----------------------- ----------------------- -----------------------
  OS                      Pre-built               Customized

  Applications            Usually need            Can be pre-installed
                          installation            

  Configuration           Default                 Organization-specific

  Standardization         Limited                 High

  Deployment              Simple                  Requires image
                                                  management

  Enterprise Workloads    Depends on requirement  Useful for standardized
                                                  workloads
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# Best Practices

-   Use Azure Compute Gallery for centralized image management.
-   Version your images.
-   Patch the source image regularly.
-   Remove unnecessary software before creating images.
-   Follow proper OS generalization procedures.
-   Test new image versions before production deployment.
-   Use separate image versions for development and production.
-   Integrate image creation with CI/CD where appropriate.
-   Avoid embedding secrets, passwords, or credentials in custom images.
-   Monitor VMSS instances after deployment.

------------------------------------------------------------------------

# Troubleshooting

## VMSS Instance Does Not Start

Check:

``` text
VM Scale Set
    |
Instances
    |
Instance Status
```

Review boot diagnostics and activity logs.

------------------------------------------------------------------------

## Application Is Not Running

Connect to the VMSS instance and check:

``` bash
sudo systemctl status nginx
```

Check logs:

``` bash
sudo journalctl -u nginx
```

------------------------------------------------------------------------

## New Instances Do Not Have Expected Configuration

Verify:

-   Correct image was selected.
-   Correct image version was selected.
-   Source VM was properly generalized.
-   VMSS model is using the expected image version.

------------------------------------------------------------------------

# Interview Questions

### What is a Custom VM Image?

A reusable VM image containing an operating system and pre-configured
applications and settings.

### Why use Custom Images with VMSS?

To create multiple consistent VM instances with the required software
and configuration already installed.

### What is Azure Compute Gallery?

A service for storing, managing, sharing, and versioning custom VM
images.

### What happens when VMSS scales out?

Azure creates additional VM instances using the VMSS model and
configured image.

### What is a Golden Image?

A standardized VM image containing the approved OS configuration,
software, security settings, and dependencies used as a deployment
baseline.

### Can VMSS use a custom image?

Yes. VMSS can be configured to deploy instances from a custom image,
including images managed through Azure Compute Gallery.

### Why should secrets not be stored in custom images?

Images can be reused across multiple instances and environments. Secrets
should instead be provided securely using services such as Azure Key
Vault or managed identities.

------------------------------------------------------------------------

# Cleanup

To avoid unnecessary Azure charges, remove the lab resources after
completing the demonstration.

``` text
Resource Group
    |
    +-- VM Scale Set
    +-- Load Balancer
    +-- Public IP
    +-- Virtual Network
    +-- Azure Compute Gallery
    +-- Custom Image Version
```

------------------------------------------------------------------------

# Author

**TechWithBSK**

Azure \| AWS \| Kubernetes \| Terraform \| Azure DevOps \| Linux

Happy Learning! 🚀
