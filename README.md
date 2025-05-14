# Detecting-Web-Attacks-with-Python
<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1: Create Two VMs
- Step 2: Connect to Each VM via SSH
- Step 3: Install Tools on Each VM
- Step 4: Build the Python WAF on the Test VM
- Step 5: Launch Attacks from the Attacker VM
- Step 6: Monitor Logs on the Victim VM

<h2>Deployment and Configuration Steps</h2>

Step 1: Create Two VMS
- Virtual Machine #1 (Victim Machine)

![Screenshot 2025-05-12 222714](https://github.com/user-attachments/assets/72a48f70-5cb6-4146-8d92-4a944179efe5)
- Purpose: Run vulnerable web app + Python WAF

Virtual Machine #2 (Attack Machine)

![Screenshot 2025-05-13 200837](https://github.com/user-attachments/assets/2d7be1f0-2a63-45eb-900d-e26bca327e97)
- Purpose: Launch simulated web attacks using curl or tools like Burp Suite, OWASP ZAP

Step 2: Connect to Each VM via SSH

- SSH Connection via VM #1 (Victim)
![Screenshot 2025-05-13 203302](https://github.com/user-attachments/assets/ec253d98-7d20-441c-99f3-3a6f11544181)
![Screenshot 2025-05-13 203322](https://github.com/user-attachments/assets/967f0bb2-f7ad-4028-9202-bf5126c008eb)

- SSH Connection via VM #2 (Attacker)
![Screenshot 2025-05-13 205035](https://github.com/user-attachments/assets/f4cc60c3-b7dd-418d-8c01-28e9bf905a0c)
![Screenshot 2025-05-13 205053](https://github.com/user-attachments/assets/c4bb68bb-c4f5-4969-a58d-1224cab59199)

Step 3: Install Tools on Each VM
-  Victim1 VM (Test Server)
-  Installing python3 & python3-pip, flask & requests (via pip3 install), apache2, sudo systemctl start apache2
![Screenshot 2025-05-13 210636](https://github.com/user-attachments/assets/0e3059f2-8877-4410-a341-f1135ebaf69b)

- Attack1 VM (Attack Machine)
- Installing the command "curl" which is a Lightweight command-line tool to simulate HTTP requests that mimic attacks (SQL injection, XSS, etc.) and allows you to test how the WAF blocks or allows traffic
![Screenshot 2025-05-13 211200](https://github.com/user-attachments/assets/e1fcb066-9c95-43a7-9024-acc1c87dcab3)

Step 4:  Build the Python WAF on the Test VM

![Screenshot 2025-05-13 213621](https://github.com/user-attachments/assets/e89f1415-2547-416f-86d6-9c6e588870c2)
![Screenshot 2025-05-13 213641](https://github.com/user-attachments/assets/9d0bdb70-ef74-41c8-8006-2151715f2c65)
![Screenshot 2025-05-13 221800](https://github.com/user-attachments/assets/fbc96480-5671-4866-9a9c-fff31bcb4d64)

The WAF is now live, listening on HTTP port 80

It's ready to intercept requests, block attacks, and forward safe traffic to the Apache backend (still running on port 8080).

Step 5: Launch Attacks from the Attacker VM

Here we launched an SQL injection attack, XXS attack, Local File Inclusion (LFI), Remote File Inclusion (RFI), Command Injection, and an IDOR attack, As you can see from the active WAF we created on the Victim VM, everything is getting detected and blocked.

![Screenshot 2025-05-13 223220](https://github.com/user-attachments/assets/eadb83a6-7ba0-4748-861e-1220a7750e59)

Step 6: Monitor Logs on the Victim VM

Here you can see the logs generated from the Attack VM and that our Python script was successfully executed blocking all the attacks.

![Screenshot 2025-05-13 223553](https://github.com/user-attachments/assets/13bca55a-5771-46cc-a970-c17c5dfb3899)












