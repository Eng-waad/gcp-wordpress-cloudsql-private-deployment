# gcp-wordpress-cloudsql-private-deployment
Deploying WordPress on Google Cloud using Cloud SQL (MySQL), connected securely via Cloud SQL Proxy and Private IP with Compute Engine
#  WordPress Deployment on GCP using Cloud SQL

##  Project Overview
This project demonstrates how to deploy a WordPress application on Google Cloud Platform (GCP) using Cloud SQL (MySQL).  
The application connects to the database using two secure methods:
- Cloud SQL Proxy
- Private IP

---

##  Architecture
- Compute Engine (2 VMs)
  - wordpress-proxy
  - wordpress-private-ip
- Cloud SQL (MySQL 8.0)
- Private VPC Network
- Cloud SQL Proxy

---

## ⚙️ What I Did (Step-by-Step)

### 1. Created Cloud SQL Instance
- MySQL 8.0
- Region: us-central1
- Enabled Private IP
- Configured machine type and storage

---

### 2. Created Database
- Database name: `wordpress`

---

### 3. Configured Cloud SQL Proxy
- Installed proxy on VM
- Connected using:
```bash
./cloud_sql_proxy -instances=$SQL_CONNECTION=tcp:3306
 4. Connected WordPress via Proxy
 • Used:
 • Host: 127.0.0.1
 • Installed WordPress successfully

 5. Connected via Private IP
 • Used internal IP instead of proxy
 • Verified connection with:
 • “Already Installed!” message

 Screenshots

(All screenshots are inside the screenshots/ folder)

 Key Learnings
 • Difference between Proxy vs Private IP
 • How to securely connect applications to Cloud SQL
 • Deploying WordPress on Compute Engine
 • Using internal networking to improve performance and security

 Final Result
 • WordPress successfully deployed
 • Connected to Cloud SQL using:
 • Proxy (secure tunneling)
 • Private IP (faster & more secure)

##  Note

In this lab, the WordPress application was configured to connect to Cloud SQL using both Cloud SQL Proxy and Private IP. While the proxy method provides a secure way to connect by tunneling traffic through localhost (127.0.0.1), it was not required for the final validation in this setup. The application successfully connected using the Private IP address, which enables a direct internal connection within the same VPC network. 

Compared to the proxy approach, Private IP offers better performance due to lower latency and reduces the attack surface by avoiding exposure to external networks. This demonstrates that while Cloud SQL Proxy is useful for secure access from external or different environments, Private IP is the preferred solution when the application and database are hosted within the same region and VPC.
