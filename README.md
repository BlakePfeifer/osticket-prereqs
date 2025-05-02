# osticket- Prereqs & Install
<p align="center">
<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>Installing osTicket - Prerequisites and Full Installation Guide</h1>

This tutorial will walk you through installing **osTicket**, a popular support ticketing system, on a **Windows 11** virtual machine.  
No previous experience needed — every step is explained in simple terms!

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



---

## Step 3: Install IIS and Dependencies

- On your VM desktop, search for **"Turn Windows features on or off"**.
- Enable:
  - **Internet Information Services (IIS)**
  - Under **World Wide Web Services** ➡️ **Application Development Features** ➡️ [X] **CGI**

![image](https://github.com/user-attachments/assets/8fbbe29c-a380-4a6e-b933-22881e83e542)


---

## Step 4: Prepare Installation Files

- Download the **osTicket-Installation-Files.zip** to your VM.
- Extract it to your **Desktop**.
- You should now have a folder called **osTicket-Installation-Files**.

![image](https://github.com/user-attachments/assets/82677340-77f7-46f0-a4a7-b0f4d1584bb0)


---

## Step 5: Install PHP Manager and Rewrite Module

- From **osTicket-Installation-Files**:
  - Install **PHP Manager for IIS** (`PHPManagerForIIS_V1.5.0.msi`).
  - Install **IIS Rewrite Module** (`rewrite_amd64_en-US.msi`).

![image](https://github.com/user-attachments/assets/7caf33a8-4a9e-48d8-a073-ebf19e6d0b5d)



---

## Step 6: Install and Configure PHP

- Create a new folder: `C:\PHP`
- From **osTicket-Installation-Files**:
  - Unzip **php-7.3.8-nts-Win32-VC15-x86.zip** into `C:\PHP`.
- Install **VC_redist.x86.exe** (important for PHP to work).

![image](https://github.com/user-attachments/assets/d55aa1eb-be79-404f-9523-c291f938a2d0)
![image](https://github.com/user-attachments/assets/2159dd56-6c23-42d2-bc5b-b6e4bb1c2524)


---

## Step 7: Install MySQL 5.5.62

- From **osTicket-Installation-Files**:
  - Install **MySQL 5.5.62** (`mysql-5.5.62-win32.msi`).
![image](https://github.com/user-attachments/assets/8d3dee4e-2767-404d-b3ef-2c32c6ba5cfd)
![image](https://github.com/user-attachments/assets/9d1605f4-9f3a-4205-a4cb-08ecdc52927f)
- During installation:
  - Choose **Typical Setup**.
  - Launch the Configuration Wizard.
![image](https://github.com/user-attachments/assets/5b801012-c853-4e85-a52e-9c1939894bfe)
![image](https://github.com/user-attachments/assets/dff6be89-f6f9-4735-9dc3-7ffb8e54524c)

   - Choose **Standard Configuration**.




![image](https://github.com/user-attachments/assets/35d80e9b-1a16-452d-ac47-0f232d7f63d8)
![image](https://github.com/user-attachments/assets/f0995704-4b46-460e-bf70-74a414e41955)
    
    - Set:   
    - **Username**: `root`
    - **Password**: `root`

![image](https://github.com/user-attachments/assets/0e088f4e-2ed0-4f41-8957-c5b94980f32b)







---

## Step 8: Configure IIS for PHP

- Open **IIS Manager** as Administrator.
- Click your server name on the left.
- Double-click **PHP Manager**.
- Click **"Register new PHP version"** and browse to:
  - `C:\PHP\php-cgi.exe`
- Stop and Start IIS to reload settings.

![image](https://github.com/user-attachments/assets/f4fffadb-8052-4e40-9d1d-73af4c693644)
![image](https://github.com/user-attachments/assets/6dad12f2-3924-44e1-abeb-6f49c499b5f5)
![image](https://github.com/user-attachments/assets/0e7da268-b4fe-4b79-b3cc-b29bf71a4808)
![image](https://github.com/user-attachments/assets/19d80bad-365e-4f50-8de1-219a4e13b875)


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

![image](https://github.com/user-attachments/assets/bf88fee3-6ded-4eb7-bda0-73537e53c01f)
![image](https://github.com/user-attachments/assets/d93fc00b-590e-406b-bd09-d804eaac0550)
![image](https://github.com/user-attachments/assets/dac8f7b7-38f6-464c-9c5f-b0f1a5465a27)
![image](https://github.com/user-attachments/assets/023f7829-221f-4812-99ed-0406c7d3d7e6)
![image](https://github.com/user-attachments/assets/16828ce8-2714-441a-b1be-e583ef8f2225)
![image](https://github.com/user-attachments/assets/0c7d6b59-1631-471d-8b48-bab92f1e0dcf)


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

![image](https://github.com/user-attachments/assets/7c2d676b-144c-4fec-a8fd-1114e53fb8e3)
![image](https://github.com/user-attachments/assets/ea1aa4a9-c543-4f68-8e6d-a663c767f1c9)
![image](https://github.com/user-attachments/assets/555d745c-064d-4df6-a302-cc5f9870c97d)
![image](https://github.com/user-attachments/assets/80e6f2a9-f6e0-4f5f-94c2-c3203c320a41)


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

![image](https://github.com/user-attachments/assets/2ab82ea4-0ff0-4343-bd76-be0d3efd54f2)
![image](https://github.com/user-attachments/assets/4b839c5f-d813-4dad-b48f-53ce969b85b3)
![image](https://github.com/user-attachments/assets/b589b621-f24c-40eb-8875-bb4483f97e8d)
![image](https://github.com/user-attachments/assets/83265ccf-9438-4984-a3ed-14b25570096a)


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

![image](https://github.com/user-attachments/assets/8893e0f6-b923-41da-b298-f1231f7b5146)
![image](https://github.com/user-attachments/assets/a68f05e9-e5f3-4989-9d5b-83e1214b21d1)


---

## Step 13: Finalize osTicket Installation

- Go back to your osTicket browser setup page.
- Fill in the database information:
  - **MySQL Database**: `osTicket`
  - **MySQL Username**: `root`
  - **MySQL Password**: `root`
- Click **Install Now!**

![image](https://github.com/user-attachments/assets/30b350f8-8969-463d-b202-4d6461c987dd)


---

# 🎉 Congratulations!

If everything was followed correctly, you should now have a working osTicket Help Desk!  
You can access:

- **Admin login page**: [http://localhost/osTicket/scp/login.php](http://localhost/osTicket/scp/login.php)
- **End User page**: [http://localhost/osTicket/](http://localhost/osTicket/)

![image](https://github.com/user-attachments/assets/72690e3e-2455-435f-b29f-8a8cb66bf917)

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


