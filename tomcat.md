# 🚀 Apache Tomcat 10.1.55 Installation on Ubuntu 24.04 (Azure VM)

## 📌 Overview

This guide explains how to install and configure Apache Tomcat 10.1.55 on Ubuntu 24.04 running on an Azure Virtual Machine.

---

# 🎯 Prerequisites

* Ubuntu 24.04 VM
* Root or Sudo Access
* Internet Connectivity
* Azure NSG allowing TCP Port 8080

---

# 🛠 Step 1: Update Server

```bash
sudo apt update
sudo apt upgrade -y
```

---

# ☕ Step 2: Install Java 21

```bash
sudo apt install openjdk-21-jdk -y
```

Verify:

```bash
java -version
```

Find JAVA_HOME:

```bash
readlink -f $(which java)
```

Expected:

```bash
/usr/lib/jvm/java-21-openjdk-amd64
```

---

# 👤 Step 3: Create Tomcat User

```bash
sudo useradd -m -U -d /opt/tomcat -s /bin/false tomcat
```

Verify:

```bash
id tomcat
```

---

# 📥 Step 4: Download Tomcat

```bash
cd /tmp

wget https://downloads.apache.org/tomcat/tomcat-10/v10.1.55/bin/apache-tomcat-10.1.55.tar.gz
```

---

# 📦 Step 5: Extract Tomcat

```bash
sudo mkdir -p /opt/tomcat

sudo tar -xzf apache-tomcat-10.1.55.tar.gz \
-C /opt/tomcat \
--strip-components=1
```

Verify:

```bash
ls /opt/tomcat
```

---

# 🔐 Step 6: Configure Permissions

```bash
sudo chown -R tomcat:tomcat /opt/tomcat

sudo chmod -R u+x /opt/tomcat/bin
```

---

# ⚙️ Step 7: Configure Systemd Service

Create:

```bash
sudo vi /etc/systemd/system/tomcat.service
```

Add:

```ini
[Unit]
Description=Apache Tomcat
After=network.target

[Service]
Type=forking

User=tomcat
Group=tomcat

Environment="JAVA_HOME=/usr/lib/jvm/java-21-openjdk-amd64"
Environment="CATALINA_PID=/opt/tomcat/temp/tomcat.pid"
Environment="CATALINA_HOME=/opt/tomcat"
Environment="CATALINA_BASE=/opt/tomcat"

ExecStart=/opt/tomcat/bin/startup.sh
ExecStop=/opt/tomcat/bin/shutdown.sh

Restart=on-failure

[Install]
WantedBy=multi-user.target
```

---

# 🔄 Step 8: Reload Systemd

```bash
sudo systemctl daemon-reload
```

---

# ▶️ Step 9: Enable & Start Tomcat

```bash
sudo systemctl enable tomcat

sudo systemctl start tomcat
```

Verify:

```bash
sudo systemctl status tomcat
```

---

# 🌐 Step 10: Configure Azure NSG

Allow:

```text
Port: 8080
Protocol: TCP
Action: Allow
```

---

# 🔥 Step 11: Access Tomcat

Get Public IP:

```bash
curl ifconfig.me
```

Open:

```text
http://PUBLIC_IP:8080
```

---

# 📋 Useful Commands

Start:

```bash
sudo systemctl start tomcat
```

Stop:

```bash
sudo systemctl stop tomcat
```

Restart:

```bash
sudo systemctl restart tomcat
```

Logs:

```bash
sudo tail -f /opt/tomcat/logs/catalina.out
```

---

# 🛠 Troubleshooting

Check Service:

```bash
sudo systemctl status tomcat -l
```

View Logs:

```bash
sudo journalctl -xeu tomcat.service
```

Verify Java:

```bash
java -version
```

Fix Permissions:

```bash
sudo chown -R tomcat:tomcat /opt/tomcat
sudo chmod +x /opt/tomcat/bin/*.sh
```

---


# 👨‍💻 Author

**TechWithBSK**

Sai Krishna Basam

DevOps & Cloud Engineer

Azure | AWS | Kubernetes | Terraform | Ansible
