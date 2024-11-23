<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Item 1
- Item 2
- Item 3
- Item 4
- Item 5

<h2>Installation Steps</h2>

Here’s a simple, step-by-step explanation of how to create an osTicket setup. I'll explain it in a straightforward way so it's easy to follow. Let’s break this into clear tasks:

---

### **1. Set Up the Virtual Machine in Azure**
1. **Create a VM in Azure**:
   - Go to Azure, create a **Windows 10** virtual machine with:
     - Name: **osticket-vm**
     - Size: **4 vCPUs** (this is like the computer’s brain capacity).
     - Username: **labuser**
     - Password: **osTicketPassword1!**
   - Finish creating the VM.

2. **Connect to the VM**:
   - Download the **Remote Desktop (RDP)** file from Azure.
   - Open it, log in using:
     - Username: **labuser**
     - Password: **osTicketPassword1!**

---

### **2. Prepare the Files**
1. **Download the Setup Files**:
   - Inside the VM, download the `osTicket-Installation-Files.zip`.
   - Extract (unzip) it to your Desktop. Name the folder **osTicket-Installation-Files**.

---

### **3. Set Up Windows Features**
1. **Enable IIS (Internet Information Services)**:
   - Open **Control Panel** > **Programs** > **Turn Windows features on or off**.
   - Find **Internet Information Services** (IIS).
   - Expand **World Wide Web Services** > **Application Development Features**.
   - Check the box for **CGI**, then click OK. This sets up the system to run websites.

---

### **4. Install Required Tools**
1. **Install PHP Manager**:
   - Go to the `osTicket-Installation-Files` folder.
   - Double-click `PHPManagerForIIS_V1.5.0.msi` to install.

2. **Install Rewrite Module**:
   - From the same folder, double-click `rewrite_amd64_en-US.msi`.

3. **Set Up PHP**:
   - Create a new folder: `C:\PHP` (like making a new folder in your computer).
   - Extract (unzip) `php-7.3.8-nts-Win32-VC15-x86.zip` into `C:\PHP`.

4. **Install Visual C++ Redistributable**:
   - Double-click `VC_redist.x86.exe` to install.

5. **Install MySQL**:
   - Run `mysql-5.5.62-win32.msi` to install MySQL (a tool to manage data).
   - Use the **Typical Setup** option.
   - During the setup wizard:
     - Choose **Standard Configuration**.
     - Set the username to **root** and the password to **root**.

---

### **5. Configure IIS**
1. **Register PHP with IIS**:
   - Open IIS (search for “IIS Manager” on the Start menu).
   - Go to **PHP Manager** and register PHP:
     - Path: `C:\PHP\php-cgi.exe`.
   - Restart IIS (click **Stop**, then **Start** the server in IIS).

---

### **6. Set Up osTicket**
1. **Install osTicket Files**:
   - Go to the `osTicket-Installation-Files` folder.
   - Unzip `osTicket-v1.15.8.zip`.
   - Copy the `upload` folder to `C:\inetpub\wwwroot`.
   - Rename the `upload` folder to **osTicket**.

2. **Open osTicket in a Browser**:
   - Go back to IIS.
   - In **Sites -> Default -> osTicket**, click **Browse *:80**.
   - This will open osTicket in your web browser. You might see a message about missing extensions (we’ll fix that).

3. **Enable PHP Extensions**:
   - In IIS, go to **PHP Manager** > **Enable or disable an extension**.
   - Enable:
     - `php_imap.dll`
     - `php_intl.dll`
     - `php_opcache.dll`.
   - Restart IIS and refresh the osTicket page.

4. **Rename the Config File**:
   - Rename this file:
     - From: `C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php`
     - To: `C:\inetpub\wwwroot\osTicket\include\ost-config.php`.

5. **Set File Permissions**:
   - Right-click `ost-config.php` > Properties.
   - Disable inheritance, remove all permissions, and give **Everyone** full access.

---

### **7. Complete Installation**
1. **Set Up osTicket in the Browser**:
   - Open the browser where osTicket is running.
   - Fill in:
     - Helpdesk Name: (e.g., **My Helpdesk**)
     - Default email: (your choice).
   - Click Continue.

2. **Create a Database**:
   - Install **HeidiSQL** from `osTicket-Installation-Files`.
   - Open HeidiSQL and connect with:
     - Username: **root**
     - Password: **root**.
   - Create a database named **osTicket**.

3. **Finish osTicket Setup**:
   - Go back to the browser and enter:
     - Database Name: `osTicket`
     - MySQL Username: `root`
     - MySQL Password: `root`.
   - Click **Install Now**.

4. **Access osTicket**:
   - Staff Login: `http://localhost/osTicket/scp/login.php`.
   - End-User Portal: `http://localhost/osTicket/`.

---

### **8. Clean Up**
1. **Delete Setup Folder**:
   - Delete `C:\inetpub\wwwroot\osTicket\setup`.

2. **Change Config File Permissions**:
   - Set `C:\inetpub\wwwroot\osTicket\include\ost-config.php` to **Read-only**.

---

And that’s it! You now have osTicket running and ready to use. 🎉
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
