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
- PHP 7.3.8
- MySQL 5.5.62
- HeidiSQL
- osTicket v1.15.8

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

## Step 3: Install IIS and Dependencies

- On your VM desktop, search for **"Turn Windows features on or off"**.
- Enable:
  - **Internet Information Services (IIS)**
  - Under **World Wide Web Services** ➡️ **Application Development Features** ➡️ [X] **CGI**

<!-- Insert Screenshot Here -->

---

## Step 4: Prepare Installation Files

- Download the **osTicket-Installation-Files.zip** to your VM.
- Extract it to your **Desktop**.
- You should now have a folder called **osTicket-Installation-Files**.

<!-- Insert Screenshot Here -->

---

## Step 5: Install PHP Manager and Rewrite Module

- From **osTicket-Installation-Files**:
  - Install **PHP Manager for IIS** (`PHPManagerForIIS_V1.5.0.msi`).
  - Install **IIS Rewrite Module** (`rewrite_amd64_en-US.msi`).

<!-- Insert Screenshot Here -->

---

## Step 6: Install and Configure PHP

- Create a new folder: `C:\PHP`
- From **osTicket-Installation-Files**:
  - Unzip **php-7.3.8-nts-Win32-VC15-x86.zip** into `C:\PHP`.
- Install **VC_redist.x86.exe** (important for PHP to work).

<!-- Insert Screenshot Here -->

---

## Step 7: Install MySQL 5.5.62

- From **osTicket-Installation-Files**:
  - Install **MySQL 5.5.62** (`mysql-5.5.62-win32.msi`).
- During installation:
  - Choose **Typical Setup**.
  - Launch the Configuration Wizard.
  - Choose **Standard Configuration**.
  - Set:
    - **Username**: `root`
    - **Password**: `root`

<!-- Insert Screenshot Here -->

---

## Step 8: Configure IIS for PHP

- Open **IIS Manager** as Administrator.
- Click your server name on the left.
- Double-click **PHP Manager**.
- Click **"Register new PHP version"** and browse to:
  - `C:\PHP\php-cgi.exe`
- Stop and Start IIS to reload settings.

<!-- Insert Screenshot Here -->

---

## Step 9: Install osTicket

- From **osTicket-Installation-Files**:
  - Unzip **osTicket-v1.15.8.zip**.
  - Copy the **upload** folder into:
    - `C:\inetpub\wwwroot\`
- Rename the folder:
  - From `upload` ➡️ to `osTicket`.

- Open IIS Manager:
  - Go to **Sites** ➔ **Default Web Site** ➔ **osTicket**.
  - On the right, click **"Browse *:80"**.

<!-- Insert Screenshot Here -->

---

## Step 10: Enable PHP Extensions

- In IIS Manager:
  - Navigate to **Default Web Site** ➔ **osTicket**.
  - Open **PHP Manager**.
  - Click **Enable or disable an extension**.
- Enable:
  - `php_imap.dll`
  - `php_intl.dll`
  - `php_opcache.dll`

- Refresh your osTicket site in the browser to see changes.

<!-- Insert Screenshot Here -->

---

## Step 11: Configure osTicket Files

- Rename the configuration file:
  - From:  
    `C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php`
  - To:  
    `C:\inetpub\wwwroot\osTicket\include\ost-config.php`

- Set permissions:
  - Right-click `ost-config.php` ➔ **Properties** ➔ **Security**.
  - **Disable Inheritance** ➔ Remove all permissions ➔ Add:
    - **Everyone** ➔ Full Control.

<!-- Insert Screenshot Here -->

---

## Step 12: Setup Database for osTicket

- From **osTicket-Installation-Files**:
  - Install **HeidiSQL**.
- Open HeidiSQL:
  - Create a new session with:
    - **Username**: `root`
    - **Password**: `root`
- Connect and create a new database:
  - Name it: `osTicket`

<!-- Insert Screenshot Here -->

---

## Step 13: Finalize osTicket Installation

- Go back to your osTicket browser setup page.
- Fill in the database information:
  - **MySQL Database**: `osTicket`
  - **MySQL Username**: `root`
  - **MySQL Password**: `root`
- Click **Install Now!**

<!-- Insert Screenshot Here -->

---

# 🎉 Congratulations!

If everything was followed correctly, you should now have a working osTicket Help Desk!  
You can access:

- **Admin login page**: [http://localhost/osTicket/scp/login.php](http://localhost/osTicket/scp/login.php)
- **End User page**: [http://localhost/osTicket/](http://localhost/osTicket/)

---

# 🧹 Clean Up

- Delete the setup folder:
  - `C:\inetpub\wwwroot\osTicket\setup`
- Set **ost-config.php** file permissions to "Read Only."

<!-- Insert Screenshot Here -->

---

# ⚡ Common Mistakes to Avoid

| Mistake | How to Avoid It |
|:---|:---|
| ❌ Wrong PHP Version | Always use PHP 7.3.8 for this setup. |
| ❌ Forgot IIS Settings | Enable CGI under Application Development Features. |
| ❌ Skipping VC_redist | Always install VC_redist.x86.exe for PHP to work. |
| ❌ Incorrect Database Setup | Always match the correct MySQL username and password (`root/root`). |
| ❌ Forgetting to Delete Setup Folder | Huge security risk if you don't delete it after install! |

---

> 🔥 **Pro Tip**: Always restart IIS after making major changes!


