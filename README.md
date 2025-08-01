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

- Create Azure Virtual machine
- Install OsTicket Installation Files
- Install MySQL 5.5.62
- Register PHP within IIS/ enable or disable extensions
- Install HeidiSQL to create a new database/session

<h2>Installation Steps</h2>

1. Create an Azure Virtual Machine using Windows 10 Pro, with 4 vCPUs.

- Name: osticket-vm - Username: labuser - Password: osTicketPassword1!

<p><img width="2553" height="1395" alt="osticket picture 1" src="https://github.com/user-attachments/assets/5edbe1a4-cb2c-493e-bbd6-2c76a88532cc" />


2. Log in to the VM with Remote Desktop using the public IP address

<img width="2559" height="1439" alt="Screenshot 2025-07-17 123220" src="https://github.com/user-attachments/assets/35b31117-be87-4f37-add3-d9caf6afc989" />

3. Within the VM (osticket-vm), download the osTicket-Installation-Files.zip and unzip it onto your desktop. The folder should be called “osTicket-Installation-Files”

- We will use the files in this folder to install osTicket and some of the dependencies.

<p><img width="2559" height="1439" alt="Screenshot 2025-07-17 134217" src="https://github.com/user-attachments/assets/b667d4bb-6b36-492e-833a-99396821cab7" />

4. Install / Enable IIS in Windows WITH CGI
- World Wide Web Services -> Application Development Features -> [X] CGI

<img width="2559" height="1439" alt="Screenshot 2025-07-17 134848" src="https://github.com/user-attachments/assets/960d297b-8a4a-4694-85f0-d8d8e66be026" />

5. From the “osTicket-Installation-Files” folder, install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi) 

- From the “osTicket-Installation-Files” folder, install the Rewrite Module (rewrite_amd64_en-US.msi)


<img width="2559" height="1439" alt="Screenshot 2025-07-17 135317" src="https://github.com/user-attachments/assets/17291e50-a3f3-4445-8acc-1c45e19f6366" />

6. Create the directory C:\PHP

- From the “osTicket-Installation-Files” folder, unzip PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into the “C:\PHP” folder

- From the “osTicket-Installation-Files” folder, install VC_redist.x86.exe.


<img width="2559" height="1439" alt="Screenshot 2025-07-17 135538" src="https://github.com/user-attachments/assets/7009f388-da02-4597-a917-a07e02da53b8" />


7. From the “osTicket-Installation-Files” folder, install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
-Typical Setup -> Launch Configuration Wizard (after install) -> Standard Configuration ->

- Username: root

- Password: root

<img width="2559" height="1439" alt="Screenshot 2025-07-17 135954" src="https://github.com/user-attachments/assets/1a379c31-7ac4-488b-bf72-d1e626b0d057" />

8. Open IIS as an Admin

- Register PHP from within IIS (PHP Manager -> C:\PHP\php-cgi.exe.)

- Reload IIS (Open IIS, Stop, and Start the server)

<img width="2559" height="1439" alt="Screenshot 2025-07-17 140438" src="https://github.com/user-attachments/assets/287bacff-e7ba-4733-a5d5-1213ea8699bb" />

9. Install osTicket v1.15.8

- From the “osTicket-Installation-Files” folder, unzip “osTicket-v1.15.8.zip” and copy the “upload” folder into “c:\inetpub\wwwroot”

- Within “c:\inetpub\wwwroot”, rename “upload” to “osTicket”

<img width="2559" height="1439" alt="Screenshot 2025-07-17 141909" src="https://github.com/user-attachments/assets/49464ca4-5697-4450-b78f-add79f4d7b27" />

10. Reload IIS (Open IIS, Stop, and Start the server)

- Go to sites -> Default -> osTicket
  
- On the right, click “Browse *:80”

- Note that some extensions are not enabled

- Go back to IIS, sites -> Default -> osTicket

- Double-click PHP Manager

- Click “Enable or disable an extension”

- Enable: php_imap.dll

- Enable: php_intl.dll

- Enable: php_opcache.dll

- Refresh the osTicket site in your browser, and observe the changes

<img width="2559" height="1439" alt="Screenshot 2025-07-17 142644" src="https://github.com/user-attachments/assets/e0c2b279-43f7-4616-ad2b-93a61cc4759a" />

11. Rename: ost-config.php

- From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php

- To: C:\inetpub\wwwroot\osTicket\include\ost-config.php


<img width="2559" height="1439" alt="Screenshot 2025-07-17 144105" src="https://github.com/user-attachments/assets/1c98bd1b-a73d-4b0f-867a-6d4a6166f283" />

12. Assign Permissions: ost-config.php

- Disable inheritance -> Remove All

- New Permissions -> Everyone -> All


<img width="2559" height="1439" alt="Screenshot 2025-07-17 144419" src="https://github.com/user-attachments/assets/e0d32ebe-e4e7-4a93-8fee-7ed6d7137e7c" />

13. From the “osTicket-Installation-Files” folder, install HeidiSQL.

- Open Heidi SQL

- Create a new session, root/root

- Connect to the session

- Create a database called “osTicket”

- Once it's installed, continue setting up osTicket in the browser

- MySQL Database: osTicket

- MySQL Username: root

- MySQL Password: root

- Click “Install Now!”



<img width="2559" height="1439" alt="Screenshot 2025-07-17 145736" src="https://github.com/user-attachments/assets/be318899-1ee8-41bf-9b96-3f7e9c41dfaa" />

14. OsTicket should now be successfully installed!


<img width="2559" height="1439" alt="Screenshot 2025-07-17 145917" src="https://github.com/user-attachments/assets/f2174041-9f5b-4bea-8eb0-571f80cfd612" />











