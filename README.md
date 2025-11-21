# MySQL Administration Lab — Module 1: Automated MySQL Deployment

A practical MySQL administration project that demonstrates real-world DBA and Linux automation skills.  
This module focuses on **fully automated installation, configuration, and user management of MySQL 8** using Ansible.

This is the first part of the full *MySQL Administration Lab*, which will later include backup & recovery, monitoring, performance tuning, and replication.

---

## 🚀 Objective

To automate the deployment of a secure, production-ready MySQL server using infrastructure-as-code techniques.

This module highlights:
- Automated MySQL installation using Ansible
- Deployment of a custom `my.cnf` server configuration
- Secure root password configuration
- Creation of database users with least-privilege access
- Idempotent, reproducible server builds

---

## 🧩 What This Module Automates

### **MySQL Installation**
- Installs MySQL Server 8 with correct system dependencies  
- Ensures `mysql` systemd service is enabled and running  
- Installs Python modules required for Ansible MySQL tasks  

### **MySQL Configuration**
- Deploys a custom configuration file (`99-custom.cnf`)  
- Sets key performance parameters:
  - `innodb_buffer_pool_size`
  - `innodb_log_file_size`
  - `max_connections`
  - `sql_mode`
- Enables binary logging (prepares for backups / replication)  

### **User & Privilege Management**
- Secures the root account with a custom password  
- Creates application and read-only users  
- Assigns proper privileges (ALL / SELECT / custom)  
- Enforces host restrictions to limit access  

### **Idempotency**
Re-running the playbook:
- Won’t recreate existing users  
- Won’t modify unchanged configs  
- Automatically restarts MySQL only if configuration changes  

---

## ⚙️ Requirements

- A Linux host (Ubuntu/Debian recommended)
- Ansible installed on your control machine
- SSH access to the target server
- MySQL 8 available through your package manager

---

## ▶️ Usage

### **1. Update the inventory**
Set the server you want to configure in `inventory.ini`.

### **2. Modify variables**
Customize:
- Root password  
- Bind address  
- Server tuning parameters  
- User accounts & privileges  

### **3. Run the playbook**
Execute:

```bash
ansible-playbook -i inventory.ini site.yml
```
