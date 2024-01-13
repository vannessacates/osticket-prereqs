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

- Free Microsoft Azure Account
- Create a Resource Group within Microsoft Azure
- Create an Azure Windows 10 Virtual Machine (VM) with 2-4 Virtual CPUs
- Remote Desktop Connection (PC) or Microsoft Remote Desktop from Apple App Store 

<h2>Installation Steps</h2>

<p>
<img src="https://github.com/vannessacates/osticket-prereqs/assets/140145473/199f02fd-e2a8-42c6-9c90-65aab471c221"/>
</p>
<p>
Start by grabbing your Public IP address from your Virtual Machine (VM) and logging in to either Remote Desktop Connection if you have a PC or Microsoft Remote Desktop if you have a MAC with the username and password you created when you originally created your VM.
</p>
<br />

<p>
<img src="https://github.com/vannessacates/osticket-prereqs/assets/140145473/62919f3e-3a95-4cc9-8c7f-70073ed31ce3"/>
</p>
<p>
Once logged in, Install/Enable IIS in Windows with CGI and Common HTTP Features. 

Do this by navigating to your control panel and clicking on Programs -> Turn Windows Features on and off

Next scroll down to Internet Information Services. Check the box, expand it, expand World Wide Web Services and expand Application Development Features -> Check off CGI. Collapse Application Development and expand Common HTTP Features -> Ensure all boxes are checked off. Press OK
</p>
<br />

<p>
<img src="https://github.com/vannessacates/osticket-prereqs/assets/140145473/4c3fae4f-dbef-4796-a6e0-7333d3e1673d"/>
</p>
<p>
To ensure the installation worked, navigate to a web browser and type in 127.0.0.1 and hit enter. Your screen should look like the image above.
</p>
<br />

<p>
<img src="https://github.com/vannessacates/osticket-prereqs/assets/140145473/d5122d7e-46a0-46f0-ad26-69d502099317"/>
</p>
<p>
Download and Install PHP Manager for IIS and Rewrite Module. Once both of those are downloaded, create a folder in C Drive titled PHP and install PHP 7.3.8 and unzip the contents into C:\PHP. Once extracted download and install VC_redist.x86.exe
</p>
<br />

<p>
<img src="https://github.com/vannessacates/osticket-prereqs/assets/140145473/c5a440e8-e968-42b7-b568-58f715f5f2d5"/>
</p>
<p>Download and Install MySQL 5.5.62. Select Typical when doing the install. Once MySQL launches, choose standard confirguration and remember the password you create as this will be used for the root username that is automatically being created.
</p>
<br />

<p>
<img src="https://github.com/vannessacates/osticket-prereqs/assets/140145473/af39b67d-6b35-471d-9663-513721f1c605"/>
</p>
<p>Open up start and type in IIS. Right click on Internet Information Services and select run as administrator. Double click on PHP and select register new PHP and browse to the PHP folder we created in C Drive, open it up and choose php-cgi. Refresh IIS to ensure changes went through.</p>
<br />

<p>
<img src="https://github.com/vannessacates/osticket-prereqs/assets/140145473/46f48780-3063-4c47-bbeb-b690e909eead"/>
</p>
<p>
Download osTicket

Extract and copy “upload” folder to c:\inetpub\wwwroot

Within c:\inetpub\wwwroot, Rename “upload” to “osTicket”
</p>
<br />

<p>
<img src="https://github.com/vannessacates/osticket-prereqs/assets/140145473/b3c227b4-b864-43c4-805e-94d66dcc504a"/>
</p>
<p>
Navigate back to IIS and run it as an administrator. Open up sites on the left, open the drop down defualt, and click on osticket. On the right hand side click on Browse *:80 

A web browser should open up to osTicket
</p>
<br />

<p>
<img src="https://github.com/vannessacates/osticket-prereqs/assets/140145473/994ae34a-facb-4645-a1a6-0832f203087c"/>
</p>
<p>Note that some extensions are not enabled
Go back to IIS, sites -> Default -> osTicket
Double-click PHP Manager
Click “Enable or disable an extension”
Enable: php_imap.dll
Enable: php_intl.dll
Enable: php_opcache.dll
Refresh the osTicket site in your browse, observe the changes
</p>
<br />

<p>
<img src="https://github.com/vannessacates/osticket-prereqs/assets/140145473/eb8dae03-bfec-40b1-ad4b-e78fed5b4d2f"/>
</p>
<p><img src="https://github.com/vannessacates/osticket-prereqs/assets/140145473/a281acf3-6bb3-447f-b6e4-37aebae936e0"/>
</p>
<p>Rename: ost-config.php
From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
To: C:\inetpub\wwwroot\osTicket\include\ost-config.php
</p>
<br />

<p> 
<img src="https://github.com/vannessacates/osticket-prereqs/assets/140145473/3b72e9be-d1cf-4167-b1e4-3d1e30d28a76"/>
</p>
<p>
Assign Permissions: ost-config.php
Disable inheritance -> Remove All
New Permissions -> Everyone -> Full Contorl
DON'T FORGET to click APPLY then OK
</p>
<p>
<img src="https://github.com/vannessacates/osticket-prereqs/assets/140145473/4fdbe9b7-0b27-4c0e-9a05-3c14fc02d91c"/>
</p>
<br />

<p><img src="https://github.com/vannessacates/osticket-prereqs/assets/140145473/5a504e36-b395-46a3-b7b5-4a52cb496d02"/>
</p>
<p><img src="https://github.com/vannessacates/osticket-prereqs/assets/140145473/9b197cbd-4fe9-4962-aab7-3621638f0bc6"/>
</p>
<p>
Launch Heidi SQL
Create a new session, and enter in the password you created earlier for root
Connect to the session
Create a database called “osTicket”
</p>
<br />

<p>
<img src="https://github.com/vannessacates/osticket-prereqs/assets/140145473/f6592fe8-b794-4dcc-909a-145b00523c1a"/>
</p>
<p>
Press continue on osTicket and fill in the information. Fill in the bottom section with database being 'osticket', username being 'root' and the password you created.
</p>
<br />

<p>
<img src="https://github.com/vannessacates/osticket-prereqs/assets/140145473/19d24b00-a544-4350-85d3-b106697bcfb4"/>
</p>
<p>Once successfully installed, you will see the congratulations screen!</p>
<br />
