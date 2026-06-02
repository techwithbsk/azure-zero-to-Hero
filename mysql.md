# 🐬 MySQL 8 Installation on Ubuntu 24.04 (Azure VM)

## 📌 Overview

This guide explains how to install and configure MySQL 8 Server on Ubuntu 24.04 running on Azure Virtual Machine.

---

# 🎯 Prerequisites

* Ubuntu 24.04 VM
* Root or Sudo Access
* Internet Connectivity

---

# 🛠 Step 1: Update Server

```bash
sudo apt update
sudo apt upgrade -y
```

---

# 📥 Step 2: Install MySQL Server

```bash
sudo apt install mysql-server -y
```

Verify Installation:

```bash
mysql --version
```

---

# ▶️ Step 3: Start MySQL Service

```bash
sudo systemctl start mysql

sudo systemctl enable mysql
```

Check Status:

```bash
sudo systemctl status mysql
```

Expected:

```text
active (running)
```

---

# 🔒 Step 4: Secure MySQL

Run:

```bash
sudo mysql_secure_installation
```

Recommended:

```text
Remove anonymous users? Y
Disallow root login remotely? Y
Remove test database? Y
Reload privilege tables? Y
```

---

# 👤 Step 5: Login to MySQL

```bash
sudo mysql
```

Check Version:

```sql
SELECT VERSION();
```

Exit:

```sql
exit;
```

---

# 🗄 Step 6: Create Database

```sql
CREATE DATABASE appdb;
```

Verify:

```sql
SHOW DATABASES;
```

---

# 👨‍💻 Step 7: Create User

```sql
CREATE USER 'appuser'@'%' IDENTIFIED BY 'StrongPassword@123';
```

Grant Access:

```sql
GRANT ALL PRIVILEGES ON appdb.* TO 'appuser'@'%';

FLUSH PRIVILEGES;
```

---

# 🌐 Step 8: Enable Remote Access (Optional)

Edit:

```bash
sudo vi /etc/mysql/mysql.conf.d/mysqld.cnf
```

Change:

```text
bind-address = 0.0.0.0
```

Restart:

```bash
sudo systemctl restart mysql
```

---

# 🔥 Step 9: Configure Azure NSG

Allow:

```text
Port: 3306
Protocol: TCP
Action: Allow
```

⚠️ For Production, allow only trusted IPs.

---

# 🧪 Step 10: Test Connectivity

From Remote Server:

```bash
mysql -h SERVER_IP -u appuser -p
```

---

# 📋 Useful Commands

Start:

```bash
sudo systemctl start mysql
```

Stop:

```bash
sudo systemctl stop mysql
```

Restart:

```bash
sudo systemctl restart mysql
```

Status:

```bash
sudo systemctl status mysql
```

Login:

```bash
sudo mysql
```

---

# 🛠 Troubleshooting

Check Logs:

```bash
sudo journalctl -u mysql
```

Verify Port:

```bash
sudo ss -tulpn | grep 3306
```

Verify Service:

```bash
sudo systemctl status mysql
```

---


# 👨‍💻 Author

**TechWithBSK**

Sai Krishna Basam

DevOps & Cloud Engineer

Azure | AWS | Kubernetes | Terraform | Ansible
