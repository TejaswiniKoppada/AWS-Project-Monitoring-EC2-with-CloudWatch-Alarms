# 🚀 AWS Project – Monitoring EC2 with CloudWatch Alarms

![AWS](https://img.shields.io/badge/AWS-Cloud-yellow) ![Time Taken](https://img.shields.io/badge/Time-45min-blue) ![Status](https://img.shields.io/badge/Status-Completed-green)

## 📌 Overview

In this project, I set up and tested an **Amazon CloudWatch Alarm** for monitoring an **EC2 instance**. The alarm was configured to track the **NetworkIn metric** and trigger when network traffic crossed a defined threshold. This gave me practical experience in monitoring AWS resources and generating alerts based on performance metrics.

---

## 👤 Author

**Tejaswini Koppada**

---

## ☁️ Cloud Service Provider

* **Amazon Web Services (AWS)**

---

## 🎯 What I Did

* Launched an **EC2 t2.micro instance** with a public IP.
* Used a **UserData script** to install an Apache server and deploy a simple webpage.
* Accessed the webpage using the instance’s public IP to generate **NetworkIn traffic**.
* Created a **CloudWatch Alarm** on the **NetworkIn metric**.
* Configured the alarm with:
  * **Period**: 5 minutes
  * **Threshold**: 5000 bytes (low value for testing)
  * **Datapoints to alarm**: 3 of 4
* Verified the alarm by refreshing the website multiple times until the threshold was breached and the alarm entered the **ALARM** state.

---

## 🛠️ Steps I Followed

### EC2 Instance Setup

* Launched a **t2.micro instance** with **Amazon Linux 2** AMI.
* Enabled auto-assign public IP for accessibility.
* Added the following **UserData script** to set up Apache and a demo webpage:

```bash
#!/bin/bash
yum update -y
yum install -y httpd
systemctl start httpd
systemctl enable httpd
echo "<h1>Welcome to Tejaswini’s CloudWatch Demo</h1>" > /var/www/html/index.html
Accessed the instance via public IP and verified the webpage loaded successfully.

Generating Network Traffic
Refreshed the webpage several times to create inbound network traffic.

Allowed the NetworkIn metric to appear in CloudWatch after a few minutes.

CloudWatch Alarm Setup
Went to CloudWatch → Alarms → Create Alarm.

Selected EC2 → Per-Instance Metrics → NetworkIn for the instance.

Configured the alarm with:

Period: 5 minutes

Threshold: 5000 bytes

Datapoints to alarm: 3 out of 4

Named the alarm EC2-NetworkIn-Alarm.

Testing the Alarm
Generated enough traffic to cross the threshold.

After about 5–10 minutes, the alarm state changed from OK → ALARM.

When traffic reduced, the alarm automatically returned to OK state.

📘 Key Learnings
A CloudWatch Alarm can monitor metrics and trigger actions when thresholds are breached.

NetworkIn is useful for testing because traffic can be generated manually.

Alarms evaluate metrics over periods and evaluation periods to avoid false alarms.

There is a small delay (5+ minutes) before metrics appear and alarms update.

📂 References
EC2 Metrics – NetworkIn

Amazon CloudWatch Alarms Documentation

💰 Cost Considerations
Used a t2.micro instance – Free Tier eligible.

CloudWatch Alarm was within Free Tier (first 10 alarms free).

⏳ Time Taken
Approximately 45 minutes.

✅ Output Screenshot


✨ This project gave me practical experience in monitoring EC2 instances with CloudWatch, setting thresholds, and testing alarms effectively.
