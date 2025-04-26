# osticket-prereqs
<p align="center">
<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>Installing osTicket - Prerequisites and Full Installation Guide</h1>

This tutorial will walk you through installing **osTicket**, a popular support ticketing system, on a **Windows 11** virtual machine.  
No previous experience needed — every step is explained in simple terms!

---

# 🎥 Video Demonstration

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

---

# 💻 Environments and Technologies Used

- Microsoft Azure (Virtual Machine)
- Windows 11
- Remote Desktop (RDP)
- Internet Information Services (IIS)
- PHP Manager for IIS
- MySQL Database
- osTicket Installer

---

# 🖥️ Operating System Used

- Windows 11 (23H2)

---

# ✅ What You Need First

- Microsoft Account
- Azure Subscription (Free Tier works)
- Internet Connection
- Remote Desktop App (comes built into Windows)

---

# 📢 Important!  
> **If you already have a Virtual Machine ready to use, you can skip ahead to [Step 3: Install IIS (Internet Information Services)](#step-3-install-iis-internet-information-services).**  
>  
> If you don't have a VM yet, start from Step 1 below!

---

# 🚀 Step-by-Step: How to Install osTicket

---

## Step 1: Create a Virtual Machine on Azure

- Go to [Azure Portal](https://portal.azure.com).
- Click **"Create a Resource"** > **"Virtual Machine"**.
- Choose:
  - **Image**: Windows 11 Pro
  - **Size**: Choose a free or low-cost option
  - **Allow Public Inbound Ports**: Yes, **RDP (3389)**
- Finish creating your VM.

![image](https://github.com/user-attachments/assets/54de4f90-3edd-4a3d-b71f-fe2a6ad9ee23)
![image](https://github.com/user-attachments/assets/db95e822-3c15-49ef-813a-a0ae8e305577)
![image](https://github.com/user-attachments/assets/2ee95131-1865-4ae8-bfd6-68ce8a4a95e3)
![image](https://github.com/user-attachments/assets/a31ef87e-dd6e-4d8c-ac03-420249b03a20)
![image](https://github.com/user-attachments/assets/f720df7d-4e5a-4493-8fd0-4aebe5e648f1)


---

## Step 2: Connect to Your Virtual Machine

- In Azure, click on your VM > **Connect** > **RDP**.
- Download the RDP file and open it.
- Enter your username and password to log in.

![image](https://github.com/user-attachments/assets/d7676a38-1f9b-4161-a0a5-4649a9bf7e22)

![image](https://github.com/user-attachments/assets/2b5ed484-e015-4681-b8f2-bf29aa80cba9)

![image](https://github.com/user-attachments/assets/b4b36afa-7104-4133-9fa4-6c3178063f19)

---

## Step 3: Install IIS (Internet Information Services)

- On your VM desktop, search for **"Turn Windows features on or off"** in the Start menu.
- Check the box for:
  - **Internet Information Services**
- Expand the IIS options and make sure these are checked:
  - Static Content
  - Default Document
  - Directory Browsing
  - HTTP Errors
  - ASP.NET
  - CGI
  - ISAPI Extensions
  - ISAPI Filters
- Click **OK** to install.

![image](https://github.com/user-attachments/assets/501aa3f0-601c-473e-ac5c-592b90c77b49)

---

## Step 4: Install PHP Manager and PHP

- Download **PHP Manager for IIS** from [here](https://www.iis.net/downloads/community/2018/05/php-manager-1-4-for-iis-10).
- Install it by following the on-screen instructions.

- Next, download **PHP for Windows** (version 7.3 or 7.4 recommended) from [here](https://windows.php.net/download/).
- Choose the **Thread Safe** version and make sure you get the correct architecture (x64 if your VM is 64-bit).

- After installing PHP:
  - Open **IIS Manager** (search for it in Start Menu).
  - Click your computer name on the left panel.
  - Open **PHP Manager** to confirm PHP is detected properly.

<!-- Insert Screenshot Here -->

---

## Step 5: Install MySQL

- Download **MySQL Community Server** from [here](https://dev.mysql.com/downloads/mysql/).
- Run the installer and follow the setup wizard.
- **Important**: Set a strong root password that you will remember.
- (Optional) You can also install **MySQL Workbench** if you want an easier visual way to manage databases.
- After installation, create a new database for osTicket:
  - Example: `osticket_db`

<!-- Insert Screenshot Here -->

---

## Step 6: Download and Install osTicket

- Download the latest version of **osTicket** from [here](https://osticket.com/download/).
- Extract the downloaded zip file.
- Move the contents into this folder:  
  `C:\inetpub\wwwroot\osTicket`

- Set permissions:
  - Right-click on the `include` and `attachments` folders > **Properties** > **Security** tab > Allow full control for IIS users.

<!-- Insert Screenshot Here -->

---

## Step 7: Run the osTicket Web Installer

- Open your web browser.
- Navigate to:  
  `http://<Your_VM_Public_IP>/osTicket`
- The osTicket setup page should appear.
- Fill out:
  - Admin Information (name, email, password)
  - Database Information (Database Name, MySQL username, password)

<!-- Insert Screenshot Here -->

---

## Step 8: Final Steps After Installation

- After installation, go to `C:\inetpub\wwwroot\osTicket`.
- **Delete or rename the `setup` folder** to protect your site.
- Double-check that the main page loads without errors.

<!-- Insert Screenshot Here -->

---

# 📝 Summary of What You Did

- Created a Windows 11 VM on Azure
- Installed a web server (IIS)
- Installed PHP and MySQL
- Set up osTicket
- Connected everything together

---

# ⚡ Common Mistakes to Avoid

| Mistake | How to Avoid It |
|:---|:---|
| ❌ Forgot RDP Port | Always allow port **3389** when creating your VM. |
| ❌ Wrong PHP Version | Use **PHP 7.3 or 7.4** — newer versions may not work with osTicket. |
| ❌ Database Connection Errors | Double-check your MySQL database name, username, and password. |
| ❌ Forgot to Delete Setup Folder | Always delete the `setup` folder for security reasons. |
| ❌ Extra VM Costs | Shut down or deallocate your VM when you’re not using it. |

---

> 🔥 **Pro Tip**: Think of your Azure VM like a hotel room — if you forget to check out, you keep getting charged!


