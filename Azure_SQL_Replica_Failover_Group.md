# Azure SQL Database - Replica & Failover Group

## Azure SQL High Availability and Disaster Recovery

### Overview

This hands-on lab demonstrates how to configure **Azure SQL Database** for disaster recovery using a **secondary replica** and an **Azure SQL Failover Group**.

The setup uses a primary Azure SQL Database and a secondary replica in another Azure region. The Failover Group provides stable listener endpoints that applications can use so connectivity can be redirected during a failover.

---

## Architecture

```text
                         Application
                              |
                              v
                    Failover Group Listener
                              |
                 +------------+------------+
                 |                         |
                 v                         v
          Primary SQL Server         Secondary SQL Server
             / Region 1                  / Region 2
                 |                         |
                 v                         v
          Primary Database             Replica Database
                 |                         |
                 +------ Replication ------+
```

## Objectives

- Create an Azure SQL Database.
- Configure a secondary replica in another Azure region.
- Create an Azure SQL Failover Group.
- Configure failover group listener endpoints.
- Test failover.
- Verify database availability after failover.
- Understand planned and unplanned failover.
- Understand failback.

## Example Setup

| Component | Example |
|---|---|
| Primary Region | East US |
| Secondary Region | West US |
| Primary SQL Server | sql-primary |
| Secondary SQL Server | sql-secondary |
| Database | appdb |
| Failover Group | app-fg |

---

# Part 1 - Create Primary Azure SQL Database

Navigate to:

```text
Azure Portal
    |
SQL databases
    |
Create
```

Example:

```text
Database Name: appdb
SQL Server: sql-primary
Region: Primary Region
```

Configure the required compute, networking, authentication, and security settings.

---

# Part 2 - Create a Secondary Replica

Configure a secondary database in another Azure region.

```text
Primary Database
      |
      | Replication
      v
Secondary Replica
```

Example:

```text
Primary:   East US
Secondary: West US
```

After configuring the replica, verify the replication relationship and health.

---

# Part 3 - Create the Failover Group

Navigate to the SQL Server:

```text
SQL Server
    |
Failover groups
    |
Create
```

Example:

```text
Failover Group: app-fg
Primary Server: sql-primary
Secondary Server: sql-secondary
```

Add the required database to the failover group.

---

# Part 4 - Configure Failover Group

Important concepts include:

```text
Failover Policy
Failover Grace Period
Read-Write Listener
Read-Only Listener
```

Choose the configuration according to the application's RTO and RPO requirements.

---

# Part 5 - Failover Group Listener

The application can connect through the failover group listener instead of directly using the primary server.

```text
Application
     |
     v
Failover Group Listener
     |
     +-------------------+
     |                   |
     v                   v
Primary Database     Secondary Database
     |                   |
     +---- Failover -----+
```

After failover, the listener redirects connections to the new primary.

---

# Part 6 - Test Failover

Navigate to:

```text
Failover Group
    |
Failover
```

After the operation completes, the secondary becomes the primary.

Verify:

- Database connectivity
- Application connectivity
- Database availability
- Listener behavior
- Replication status

---

# Part 7 - Failback

When the original primary region is healthy and ready, move the workload back according to the DR procedure.

```text
Region 1
 Primary
    |
    | Failover
    v
Region 2
 Primary
    |
    | Failback
    v
Region 1
 Primary
```

Validate synchronization and application readiness before failback.

---

# Replica vs Failover Group

| Feature | Replica / Geo-Replication | Failover Group |
|---|---|---|
| Secondary Database | Yes | Uses secondary database |
| Cross-Region DR | Yes | Yes |
| Database Replication | Yes | Yes |
| Failover Management | Database-level | Group-level |
| Listener Endpoint | No dedicated failover-group listener | Yes |
| Application Connection Redirection | Requires application handling | Simplified through listener |

---

# Planned vs Unplanned Failover

## Planned Failover

Useful for:

- Maintenance
- DR testing
- Controlled regional migration
- Planned operations

## Unplanned / Forced Failover

Used when the primary environment is unavailable and recovery is required.

```text
Primary Region Failure
        |
        v
Failover Group
        |
        v
Secondary Region
        |
        v
Application Recovery
```

---

# Real-World Use Cases

- Regional disaster recovery
- Business continuity
- Planned maintenance
- Application resilience
- Cross-region database protection

---

# Best Practices

- Choose a secondary region appropriate for business continuity requirements.
- Test failover regularly.
- Monitor replication health.
- Use the failover group listener for application connectivity where appropriate.
- Define RTO and RPO requirements.
- Document failover and failback procedures.
- Test application behavior after failover.
- Protect credentials and connection strings.
- Monitor Azure SQL health and alerts.

---

# Troubleshooting

## Replica Is Not Healthy

Check:

```text
Primary Database
    |
Replication
    |
Replication Health
```

Review Azure SQL monitoring and activity logs.

## Application Cannot Connect After Failover

Verify:

- Application connection string
- Failover group listener
- DNS/connectivity
- Firewall/network rules
- Authentication
- Database availability

## Failover Is Not Available

Check:

- Secondary database status
- Replication health
- Failover group configuration
- Server configuration
- Permissions

---

# Interview Questions

### What is Azure SQL geo-replication?

It provides a secondary copy of an Azure SQL Database in another region for disaster recovery and other scenarios.

### What is an Azure SQL Failover Group?

A failover group manages failover between databases across SQL servers and provides listener endpoints for application connectivity.

### Why use a Failover Group?

It provides stable listener endpoints and simplifies application connection redirection during failover.

### What happens during failover?

The secondary database becomes the primary, and applications using the failover group listener can connect to the new primary.

### What is failback?

Failback moves the workload back to the original primary region after it is healthy and ready.

---

# End-to-End Flow

```text
Create Azure SQL Database
          |
          v
Configure Secondary Replica
          |
          v
Verify Replication
          |
          v
Create Failover Group
          |
          v
Configure Listener
          |
          v
Test Failover
          |
          v
Secondary Becomes Primary
          |
          v
Verify Application
          |
          v
Failback When Required
```

---

# Cleanup

Remove resources that are no longer required to avoid unnecessary Azure charges.

```text
Resource Group
    |
    +-- Primary SQL Server
    +-- Secondary SQL Server
    +-- Primary Database
    +-- Secondary Database
    +-- Failover Group
```

---

# Author

**TechWithBSK**

Azure | AWS | Kubernetes | Terraform | Azure DevOps | Linux

Happy Learning! 🚀
