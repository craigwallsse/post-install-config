<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Post-Install Configuration</h1>
This tutorial outlines the post-install configuration of the open-source help desk ticketing system osTicket.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)
- MySQL

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>Post-Install Configuration Objectives</h2>

- Install/Enable IIS in Windows with CGI and Common HTTP Features
- Insall PHP Manager for IIS <strong>(web server used to host osTicket)</strong>
- Download and install Rewrite Module <strong>(helps manage URL request in osTicket)</strong>
- Create directory C:\PHP
- Download PHP 7.3.8 and unzip into C:\PHP
- Download and install VC redist.x86 <strong>(osTicket relies on that contains C++ libraries for application execution and runtime compnents)</strong>
- Downlaod and install MySQL
- Download and install osTicket
- Assign permissions to ost-config.php
- Download and install HeidiSQL <strong>(database management tool with GUI)</strong>
- Configure osTicket in browser

<h2>Configuration Steps</h2>

<h2>Install and enable IIS in Windows with CGI and Common HTTP Features</h2>

<p>
<img src="https://i.imgur.com/ETnc6Mt.jpeg" height="80%" width="80%" alt="Image of IIS landing page"/>
</p>
<p>
IIS was installed and enabled in Windows with CGI and Common HTTP Features. Specifically, under World Wide Web Services -> Application Development Features, both CGI and Common HTTP Features were selected. Additionally, the IIS Management Console was installed by selecting IIS Management Console under Internet Information Services -> Web Management Tools. 

From the installation files, PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi) was downloaded and installed. Similarly, the Rewrite Module (rewrite_amd64_en-US.msi) was downloaded and installed. 

A directory named C:\PHP was created, and from the installation files, PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) was downloaded and unzipped into the C:\PHP directory.
</p>
<br />

<h2>Install MySQL and Install/Register PHP within IIS</h2>
<p>
<img src="https://i.imgur.com/4E9CwVD.jpeg" height="80%" width="80%" alt="Image of MySQL start up wizard"/>
</p>
<p>
I downloaded and installed MySQL 5.5.62 (mysql-5.5.62-win32.msi) using the Typical Setup to serve as the database server. After installation, I launched the Configuration Wizard, and the Standard Configuration was selected with the password assigned. I opened IIS as an administrator, and PHP was registered within IIS. Finally, IIS was reloaded by stopping and starting the server..
</p>
<br />

<h2>Install MySQL and Install/Register PHP within IIS</h2>

<p>
<img src="https://i.imgur.com/r21HRRl.jpeg" height="80%" width="80%" alt="Image of osTicket start up page"/>
</p>
<p>
I installed osTicket v1.15.8 by downloading it from the Installation Files folder. I extracted the "upload" folder and copied it to `c:\inetpub\wwwroot`, then renamed it to "osTicket." I reloaded IIS by stopping and starting the server. I navigated to sites -> Default -> osTicket and clicked "Browse *:80" on the right. 
</p>
  
<p>
<img src="https://i.imgur.com/9O1d9D8.jpeg" height="80%" width="80%" alt="Image of osTicket configuration"/>
</p>
<p>
Noticing that some extensions were not enabled, I went back to IIS, navigated to sites -> Default -> osTicket, and double-clicked PHP Manager. I enabled the extensions `php_imap.dll`, `php_intl.dll`, and `php_opcache.dll`. After refreshing the osTicket site in the browser, I observed the changes.
</p>

<p>
<img src="https://i.imgur.com/LgFvEze.jpeg" height="80%" width="80%" alt="Image of osTicket updated configurtation"/>
</p>
<p>
I then renamed `ost-sampleconfig.php` to `ost-config.php` in `C:\inetpub\wwwroot\osTicket\include`. I assigned permissions to `ost-config.php` by disabling inheritance, removing all existing permissions, and adding new permissions for "Everyone" with full control. Finally, I continued setting up osTicket in the browser, naming the helpdesk and providing a default email to receive emails from customers.
</p>
<br />

<p>
<img src="https://i.imgur.com/zdb5v0S.jpeg" width="80%" alt="Image of osTicket updated configurtation"/>
</p>
<p>
<img src="https://i.imgur.com/E49WF79.jpeg" width="80%" alt="Image of osTicket updated configurtation"/>
</p>
<p>
I downloaded and installed HeidiSQL. After opening HeidiSQL, I created a new session using the username "root" and the password "Password1" and then connected to the session. I created a database called "osTicket." Continuing with the osTicket setup in the browser, I specified the MySQL database as "osTicket," with the MySQL username "root" and the password "Password1." Finally, I clicked "Install Now!" to complete the installation.
</p>
<br />
