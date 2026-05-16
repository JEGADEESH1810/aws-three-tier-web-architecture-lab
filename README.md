# AWS Three-Tier Web Application Deployment (Lab Project)

## 📌 Overview
This project demonstrates a simulated three-tier architecture deployed on AWS using EC2, VPC, IAM, and Security Groups. The goal is to understand how scalable and secure cloud applications are designed.

This is a **hands-on learning project / lab setup** for practicing AWS cloud fundamentals.

---

## 🏗️ Architecture

### Layers:
1. **Presentation Layer (Web Tier)**
   - EC2 instance (Apache/Nginx web server)
   - Public subnet

2. **Application Layer (App Tier)**
   - EC2 instance running backend logic
   - Private subnet

3. **Database Layer (DB Tier)**
   - Amazon RDS (MySQL) or simulated DB instance
   - Private subnet

---

## 🧱 AWS Services Used
- Amazon EC2
- Amazon VPC
- Subnets (Public & Private)
- Internet Gateway
- Route Tables
- Security Groups
- IAM Roles
- (Optional) Amazon RDS

---

## 🔐 Security Design
- Web server accessible via HTTP/SSH (restricted IP)
- App and DB layers placed in private subnet
- IAM roles used for EC2 access control
- Security Groups restrict traffic between tiers

---

## ⚙️ Setup Steps

### 1. Create VPC
- CIDR: 10.0.0.0/16

### 2. Create Subnets
- Public Subnet (Web Tier): 10.0.1.0/24
- Private Subnet (App Tier): 10.0.2.0/24
- Private Subnet (DB Tier): 10.0.3.0/24

### 3. Internet Gateway
- Attach IGW to VPC

### 4. Route Tables
- Public route table → Internet Gateway
- Private route tables → no direct internet access

---

### 5. Launch EC2 Instances

#### Web Tier
- Amazon Linux 2 / Ubuntu
- Public subnet
- Enable HTTP + SSH

Install Apache:
```bash
sudo apt update -y
sudo apt install apache2 -y
sudo systemctl start apache2
