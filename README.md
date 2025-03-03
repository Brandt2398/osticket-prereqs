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

- IIS with CGI and Common HTTP Features
- IIS Management Console
- PHP Manager for IIS
- Rewrite Modle
- PHP 7.3.8
- VC-redist.x86.exe
- MySQL 5.5.62
- osTicket 

<h2>Installation Steps</h2>

<p>In Azure, create a resource group, a Windows 10 Virtual Machine, and a Virtual Network (Vnet).
<img width="1439" alt="image" src="https://github.com/user-attachments/assets/ee3d2ae0-d81f-48b1-b5b6-5d2ade44a4da" />

</p>
<p>
Next just connect to your newly created VM using RDP and using the public IPv4 address. If you are a Mac user you will have to download Microsoft RDP.
</p>
<br />

<p>
<img width="316" alt="image" src="https://github.com/user-attachments/assets/84fbac5b-0363-407b-a808-8cc13f6af3cc" />

</p>
<p>
Now that you are connected to your VM you will have to enable IIS. Simply access the control panel then select uninstall a program. Off to the left select "Turn windows features on or off". A list will appear then you will enable Internet Information Services.</p>
<br />

<p>
<img width="1580" alt="osTicket setup 3" src="https://github.com/user-attachments/assets/e518a3d6-f9b3-4999-a980-def218f74138" />
</p>

<p>Next from the osTicket-Installation Files folder we're gonna install PHP Manager for IIS</p>
<img width="1001" alt="image" src="https://github.com/user-attachments/assets/48a2e3b9-00cd-4023-8c66-5cdc77371e88" />

<p>Next create the directory C;\PHP</p>

<img width="1033" alt="image" src="https://github.com/user-attachments/assets/71c009b1-1b6b-4dfe-9abb-ba360dac4a3c" />

<p>From the “osTicket-Installation-Files” folder, unzip PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into the “C:\PHP” folder
</p>

<p>From the “osTicket-Installation-Files” folder, install VC_redist.x86.exe.</p>

<img width="1059" alt="image" src="https://github.com/user-attachments/assets/970a53ad-06ad-4b9d-9f1a-8ccaa989ad09" />

<p>Now from the “osTicket-Installation-Files” folder, install MySQL 5.5.62 (mysql-5.5.62-win32.msi)</p>
<img width="1112" alt="image" src="https://github.com/user-attachments/assets/e077065b-14f0-4e71-a67f-1604b083aac3" />

<p>Typical Setup ->
Launch Configuration Wizard (after install) ->
Standard Configuration ->
Username: root
Password: root
</p>

<p>Open IIS as an Admin, Register PHP from within IIS (PHP Manager -> C:\PHP\php-cgi.exe). Reload IIS (Open IIS, Stop and Start the server)
</p>
<img width="704" alt="image" src="https://github.com/user-attachments/assets/19383518-27d0-430d-b322-f15cc7b5fae5" />

<p>Install osTicket v1.15.8
From the “osTicket-Installation-Files” folder, unzip “osTicket-v1.15.8.zip” and copy the “upload” folder into “c:\inetpub\wwwroot”
Within “c:\inetpub\wwwroot”, Rename “upload” to “osTicket”
</p>
<img width="901" alt="image" src="https://github.com/user-attachments/assets/bc41c608-08d3-4b2c-83c1-7bdf93395dc4" />

<p>Go to sites -> Default -> osTicket
On the right, click “Browse *:80”

Note that some extensions are not enabled
Go back to IIS, sites -> Default -> osTicket
Double-click PHP Manager
Click “Enable or disable an extension”
Enable: php_imap.dll
Enable: php_intl.dll
Enable: php_opcache.dll
Refresh the osTicket site in your browser, observe the changes
</p>
<img width="830" alt="image" src="https://github.com/user-attachments/assets/f87b015e-86d4-45b4-aa9d-7f6edd9aa111" />

<p>Rename: ost-config.php
From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
To: C:\inetpub\wwwroot\osTicket\include\ost-config.php

Assign Permissions: ost-config.php
Disable inheritance -> Remove All
New Permissions -> Everyone -> All
</p>
<img width="973" alt="image" src="https://github.com/user-attachments/assets/0d6b4f8d-9ffd-4f38-bcda-b8acf22b369a" />

<p>Continue Setting up osTicket in the browser (click Continue)
Name Helpdesk
Default email (receives email from customers)
</p>
<p>From the “osTicket-Installation-Files” folder, install HeidiSQL.
Open Heidi SQL
Create a new session, root/root
Connect to the session
Create a database called “osTicket”
</p>
<img width="584" alt="image" src="https://github.com/user-attachments/assets/4f7315e0-751e-45f4-bd54-d6f2b4f967dd" />
<img width="764" alt="image" src="https://github.com/user-attachments/assets/e09f9c4a-be93-4ac0-b91b-6d00873ffe67" />
<p>Continue Setting up osTicket in the browser
MySQL Database: osTicket
MySQL Username: root
MySQL Password: root
Click “Install Now!”
</p>
<img width="675" alt="image" src="https://github.com/user-attachments/assets/261593ba-47db-49ec-8e57-c9fa4c07d186" />

<p>Congratulations, hopefully it is installed with no errors!
Browse to your help desk login page: http://localhost/osTicket/scp/login.php

End Users osTicket URL:
http://localhost/osTicket/
</p>





