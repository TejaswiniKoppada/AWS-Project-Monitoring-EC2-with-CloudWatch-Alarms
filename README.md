# AWS-Project-Monitoring-EC2-with-CloudWatch-Alarms
🚀 AWS Project – Monitoring EC2 with CloudWatch Alarms
📌 Overview

This project demonstrates how to set up and test an Amazon CloudWatch Alarm for monitoring an EC2 instance. The alarm is configured to track the NetworkIn metric and trigger when network traffic crosses a defined threshold.

By the end of this project, you will have hands-on experience with EC2, CloudWatch metrics, and alarms, as well as an understanding of how to use alarms for monitoring and automated responses.

👤 Author

Tejaswini Koppada

☁️ Cloud Service Provider

Amazon Web Services (AWS)

🎯 Project Objectives

Launch an EC2 instance with a public IP.

Deploy a simple Apache-based website using a UserData script.

Generate NetworkIn traffic by visiting the website.

Create and configure a CloudWatch Alarm on the EC2 NetworkIn metric.

Test the alarm by triggering and returning it to normal state.

🛠️ Step-by-Step Implementation
Step 1: Launch an EC2 Instance

Sign in to the AWS Management Console.

Go to EC2 → Instances → Launch Instances.

Configure the instance:

Name: cloudwatch-demo

AMI: Amazon Linux 2 (Free Tier eligible)

Instance Type: t2.micro

Key Pair: Create/select a key pair

Network Settings: Enable Auto-assign Public IP

User Data Script:

#!/bin/bash
yum update -y
yum install -y httpd
systemctl start httpd
systemctl enable httpd
echo "<h1>Welcome to Tejaswini’s CloudWatch Demo</h1>" > /var/www/html/index.html


Review and Launch the instance.

Step 2: Access the Website

Copy the Public IPv4 address of your instance.

Open a browser and visit:

http://<Public-IP>


Refresh the page multiple times to generate NetworkIn traffic.

Step 3: Create a CloudWatch Alarm

Navigate to CloudWatch → Alarms → Create Alarm.

Select Metric:

Choose EC2 → Per-Instance Metrics → NetworkIn.

Select your EC2 instance.

Define Conditions:

Period: 5 minutes

Threshold type: Static

Threshold: 5000 bytes (low threshold for easy testing)

Datapoints to alarm: 3 of 4

Configure Actions (optional but recommended):

Create or select an SNS Topic to send email/SMS notifications.

Name the alarm: EC2-NetworkIn-Alarm

Click Create Alarm.

Step 4: Trigger and Test the Alarm

Generate traffic by repeatedly refreshing the website.

Wait 5–10 minutes (CloudWatch metrics update with some delay).

The alarm will transition between states:

OK → normal traffic

ALARM → when threshold is breached

INSUFFICIENT DATA → when insufficient metrics are available

📘 Key Concepts

CloudWatch Alarm: A monitoring feature that watches metrics and triggers actions when thresholds are crossed.

Metric: A time-ordered set of data points about AWS resources (e.g., NetworkIn, CPUUtilization).

Threshold: The defined value that triggers an alarm when crossed.

Period: The time interval over which metrics are aggregated.

Evaluation Periods: The number of periods evaluated before alarm triggers (e.g., 3 of 4).

📂 References

EC2 Metrics – NetworkIn

Amazon CloudWatch Alarms Documentation

💰 Cost Considerations

t2.micro instance – Free Tier eligible

First 10 CloudWatch Alarms – Free Tier eligible

⏳ Estimated Time to Complete

~ 45 minutes

✅ Example Output

✨ Congratulations! You have successfully created and tested a CloudWatch Alarm to monitor the NetworkIn metric for an EC2 instance.

Would you like me to also add a bonus section with AWS CLI commands so that the entire process (EC2 launch + CloudWatch alarm creation) can be automated instead of using the console?

You said:
i want it like in this way i have done not like do this way you can also do i just want to represent my work
ChatGPT said:

Got it ✅
You want the README to represent the work you already completed — more like a project report (what you did), not a tutorial or guide ("do this, do that").

Here’s a rewritten version in that style:

🚀 AWS Project – Monitoring EC2 with CloudWatch Alarms
📌 Overview

In this project, I set up and tested an Amazon CloudWatch Alarm for monitoring an EC2 instance. The alarm was configured to track the NetworkIn metric and trigger when network traffic crossed a defined threshold. This helped me understand how CloudWatch can be used to monitor AWS resources and generate alerts based on performance metrics.

☁️ Cloud Service Provider

Amazon Web Services (AWS)

🎯 What I Did

Launched an EC2 t2.micro instance with a public IP.

Used a UserData script to install an Apache server and deploy a simple webpage.

Accessed the webpage using the instance’s public IP to generate NetworkIn traffic.

Created a CloudWatch Alarm on the NetworkIn metric.

Configured the alarm with:

Period: 5 minutes

Threshold: 5000 bytes (low value for testing)

Datapoints to alarm: 3 of 4

Verified the alarm by refreshing the website multiple times until the threshold was breached and the alarm entered the ALARM state.

🛠️ Steps I Followed
EC2 Instance Setup

I launched a t2.micro instance with Amazon Linux 2 AMI.

I enabled auto-assign public IP for accessibility.

In the UserData section, I added the following script to set up Apache and a demo webpage:

#!/bin/bash
yum update -y
yum install -y httpd
systemctl start httpd
systemctl enable httpd
echo "<h1>Welcome to Tejaswini’s CloudWatch Demo</h1>" > /var/www/html/index.html


Once launched, I copied the public IPv4 address and opened it in a browser. The custom webpage loaded successfully.

Generating Network Traffic

I refreshed the webpage several times to create inbound network traffic.

This allowed the NetworkIn metric to appear in CloudWatch after a few minutes.

CloudWatch Alarm Setup

I went to CloudWatch → Alarms → Create Alarm.

I selected the EC2 → Per-Instance Metrics → NetworkIn for my instance.

I configured the alarm with:

Period: 5 minutes

Threshold: 5000 bytes

Datapoints to alarm: 3 out of 4

I named the alarm EC2-NetworkIn-Alarm.

Testing the Alarm

By visiting the website repeatedly, I generated enough traffic to cross the threshold.

After about 5–10 minutes, the alarm state changed from OK → ALARM.

Once the traffic reduced, the alarm automatically went back to OK state.

📘 Key Learnings

A CloudWatch Alarm can monitor metrics and trigger actions when thresholds are breached.

NetworkIn is a useful metric to test alarms because traffic can be easily generated.

CloudWatch alarms evaluate metrics over periods and evaluation periods to avoid false alarms.

There is always a small delay (5+ minutes) before metrics appear and alarms update.

📂 References

EC2 Metrics – NetworkIn

Amazon CloudWatch Alarms Documentation

💰 Cost Considerations

I used a t2.micro instance – Free Tier eligible.

The CloudWatch Alarm was also within the Free Tier (first 10 alarms free).


✅ Output Screenshot

<img width="1920" height="911" alt="Image (1)" src="https://github.com/user-attachments/assets/a37ddb98-2327-4ff2-85f2-3c83b80dc5b8" />

✨ This project gave me practical experience in monitoring EC2 instances with CloudWatch, setting thresholds, and testing alarms effectively.
