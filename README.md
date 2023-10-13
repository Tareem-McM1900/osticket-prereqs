<p align="center">
<img src="https://i.imgur.com/8FKKXT1.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites, Installation and Configuration</h1>
This tutorial highlights the Prerequisites, Installation and Configuration of the open-source help desk ticketing system osTicket.<br />


<h2>Repersentation of osTicket on a Virtual Machine</h2>


<p>
<img src="https://i.imgur.com/7v7wiEl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)
- PowerShell

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>Prerequisites, Installation Steps</h2>

- Step 1: Create a Windows 10 Virtual Machine in Azure

Sign into your Azure portal.

Click on "Create a resource."

Search for "Windows 10 Pro" in the Azure VM setup.

Configure the virtual machine settings as follows:

Name: Vm-OsTicket
Username: StarLabsUser
Password: osTicketPassword1
VM Size: Choose one with 4 vCPUs.
Configure the network settings, storage, and other options as needed.

Click "Review + Create" and then "Create" to deploy the VM.

- Step 2: Enable IIS with CGI and Common HTTP Features

Once the Windows 10 VM is deployed, log in using the specified username and password.

Open PowerShell as an administrator.

Install the IIS role and required features:
<p>
<img src="https://i.imgur.com/htpa4vC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

- Step 3: Install PHP

Download and install PHP for Windows. Choose the appropriate version (e.g., PHP 7.4) from the PHP Windows downloads page: https://windows.php.net/download/

Extract the PHP files to a directory of your choice (e.g., C:\PHP).

Add the PHP directory to the system's PATH environment variable.

Register PHP with IIS:
<p>
<img src="https://i.imgur.com/CBuS5D8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
- Step 4: Install HeidiSQL

Download the HeidiSQL installer for Windows: https://www.heidisql.com/download.php

Run the installer and follow the installation instructions.

- Step 5: Download and Configure osTicket

Download the latest osTicket package (ZIP format) from the official website: https://osticket.com/download/

Extract the osTicket files to the IIS web root directory (e.g., C:\inetpub\wwwroot\osticket).

Create a MySQL database for osTicket using HeidiSQL database management tool.
Open Heidi SQL
Create a new session, root/Password1
Connect to the session
Create a database called “osTicket”

Open a web browser on your Windows 10 VM and access the osTicket installation page by entering the following URL:
Continue Setting up osticket in the browser.
MySQL Database: osTicket
MySQL Username: root
MySQL Password: Password1
Click “Install Now!”

Note: There are several ways to set this part up. What worked for me was:

1. Database Setup: Create a database and user for osTicket. For MySQL, use the following commands:

bashCopy code

mysql -u root -p CREATE DATABASE osticketdb; CREATE USER 'osticketuser'@'localhost' IDENTIFIED BY 'your_password'; GRANT ALL PRIVILEGES ON osticketdb.* TO 'osticketuser'@'localhost'; FLUSH PRIVILEGES; EXIT; 

2. Configuration: Access osTicket via a web browser (e.g., http://your_server_ip/osticket) to complete the installation and configure settings.

Follow the on-screen instructions to complete the osTicket setup, including database configuration.



<p>
<img src="https://i.imgur.com/oroGlKc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

<h2>My Closing Remarks</h2>
   
Setting up osTicket can be a straightforward process when you follow the right steps and prerequisites as well as having the necessary resources in place. Whether you're deploying it on a virtual machine in Azure, a dedicated server, or any other hosting environment, osTicket offers a robust solution for managing customer support inquiries.

Remember that the key to a successful osTicket setup includes:

1.	Adequate Server Resources: Ensure that your server or VM meets the system requirements, including web server, PHP, and database, to run osTicket efficiently.
2.	Proper Configuration: Carefully configure your web server, database, and PHP settings to align with osTicket's requirements.
3.	Security: Implement security best practices to protect sensitive customer data and maintain the integrity of your support system.
4.	Regular Updates: Keep osTicket and its dependencies up to date to benefit from the latest features and security enhancements.
5.	Testing: Thoroughly test your osTicket installation to ensure that it's working as expected for both support agents and end-users.

By following these guidelines, you can create a reliable and efficient customer support system with osTicket, helping your organization deliver excellent customer service.


