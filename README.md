<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>

<h1>osTicket – Prerequisites and Installation</h1>

<p>
This project documents the complete installation and configuration of <strong>osTicket</strong>, 
an open-source help desk ticketing system, using <strong>Windows 10</strong>, 
<strong>Internet Information Services (IIS)</strong>, <strong>PHP</strong>, and <strong>MySQL</strong>.
</p>

<p>
The goal of this project is to demonstrate practical system administration skills, 
including web server configuration, dependency management, database setup, and application deployment.
</p>


<h2>Environments and Technologies Used</h2>

<ul>
  <li>VMWare (Virtual Machines)</li>
  <li>Internet Information Services (IIS)</li>
  <li>PHP</li>
  <li>MySQL</li>
</ul>
<br />
<h2>Operating Systems Used</h2>

<ul>
  <li>Windows 10</li>
</ul>

<br />

<h2>List of Prerequisites</h2>

  <a href="https://drive.google.com/file/d/1-sN-hbwNLs_w2xcEH9bBaKldTCsZmdKw/view?usp=sharing">you can download prerequisites from here</a>
  <br>

<ul>
  <li>PHPManagerForIIS_V1.5.0</li>
  <li>VC_redist.x86.exe</li>
  <li>mysql-5.5.62-win32.msi</li>
  <li>rewrite_amd64_en-US.msi</li>
  <li>php-7.3.8-nts-Win32-VC15-x86.zip</li>
  <li>HeidiSQL</li>
  <li>osTicket v1.15.8</li>
</ul>
<br />


<h2>Installation Steps</h2>

<p>
<img src="https://i.imgur.com/xM5r8VR.png" width="100%" alt="Internet Information Services"/>
</p>

<p>
Open the Control Panel and navigate to:
</p>

<p>
<strong>Programs → Programs and Features → Turn Windows features on or off</strong>
</p>

<p>
Enable <strong>Internet Information Services (IIS)</strong>, then expand:
</p>

<p>
<strong>World Wide Web Services → Application Development Features → CGI</strong>
</p>

<p>
Click <strong>OK</strong> and wait for Windows to apply the changes.
</p>

<br />

<p>
<img src="https://i.imgur.com/TY4fKak.png" width="100%" alt="IIS Test Page"/>
</p>

<p>
After the changes are applied, open a web browser and navigate to:
</p>

<p>
<strong>127.0.0.1</strong>
</p>

<p>
If IIS is configured correctly, the default IIS web page should be displayed.
</p>

<img src="https://i.imgur.com/hSTgpN2.png" width="100%" alt="IIS Test Page"/>

<h3>Install Required Dependencies</h3>

<p>
Install <strong>PHPManagerForIIS_V1.5.0</strong>.  
Accept all default options and continue clicking <strong>Next</strong> until installation completes.
</p>

<p>
Install <strong>rewrite_amd64_en-US.msi</strong> (URL Rewrite Module for IIS).  
Accept all defaults and complete the installation.
</p>

<p>
Create the following directory:
</p>

<p>
<strong>C:\PHP</strong>
</p>

<p>
Extract <strong>php-7.3.8-nts-Win32-VC15-x86.zip</strong> into the <strong>C:\PHP</strong> folder.
</p>

<p>
Install <strong>VC_redist.x86.exe</strong> and complete the setup using default settings.
</p>

<img src="https://i.imgur.com/E4Sx7l6.png" width="100%" alt="IIS Test Page"/>

<img src="https://i.imgur.com/NZzyPMK.png" width="100%" alt="IIS Test Page"/>

<h3>Install and Configure MySQL</h3>

<p>
Install <strong>MySQL 5.5.62</strong>.  
Once installation finishes, check <strong>“Launch MySQL Configuration Wizard”</strong> and click <strong>Finish</strong>.
</p>

<p>
Choose <strong>Standard Configuration</strong> and leave all settings as default.
</p>
<img src="https://i.imgur.com/mfD7Ama.png" width="100%" alt="Internet Information Services"/>

<p>
Set the root password to:
</p>

<p>
<strong>Username:</strong> root<br />
<strong>Password:</strong> root
</p>

<img src="https://i.imgur.com/FTKFgBG.png" width="100%" alt="Internet Information Services"/>

<p>
Click <strong>Execute</strong> and wait for the configuration to complete.
</p>

<br />

<h3>Configure PHP in IIS</h3>

<p>
Open <strong>IIS Manager</strong> as an Administrator.
</p>

<p>
Navigate to:
</p>

<p>
<strong>PHP Manager → Register new PHP version</strong>
</p>
<img src="https://i.imgur.com/V4rEQBM.png" width="100%" alt="IIS Test Page"/>
<p>
Select:
</p>

<p>
<strong>C:\PHP\php-cgi.exe</strong>
</p>
<img src="https://i.imgur.com/KYlUXUr.png" width="100%" alt="IIS Test Page"/>
<p>
Restart IIS by selecting <strong>Stop</strong>, then <strong>Start</strong>.
</p>

<br />

<h3>Install osTicket</h3>

<p>
Extract <strong>osTicket-v1.15.8.zip</strong>.
</p>

<p>
Copy the extracted folder into:
</p>

<p>
<strong>C:\inetpub\wwwroot</strong>
</p>

<p>
Rename the <strong>upload</strong> folder to:
</p>

<p>
<strong>osTicket</strong>
</p>
<img src="https://i.imgur.com/ns5Bubd.png" width="100%" alt="IIS Test Page"/>
<p>
Restart the IIS server.
</p>

<p>
In IIS Manager, navigate to:
</p>

<p>
<strong>Sites → Default Web Site → osTicket</strong>
</p>

<p>
Click <strong>Browse *:80</strong>.
</p>
<img src="https://i.imgur.com/h9BSSW4.png" width="100%" alt="IIS Test Page"/>
<br />

<h3>Enable Required PHP Extensions</h3>

<p>
In IIS, navigate to:
</p>

<p>
<strong>Sites → Default Web Site → osTicket → PHP Manager</strong>
</p>
<img src="https://i.imgur.com/SBV9f2Z.png" width="100%" alt="IIS Test Page"/>
<p>
Select <strong>Enable or disable an extension</strong> and enable the following:
</p>

<ul>
  <li>php_imap.dll</li>
  <li>php_intl.dll</li>
  <li>php_opcache.dll</li>
</ul>
<img src="https://i.imgur.com/RSOn462.png" width="100%" alt="IIS Test Page"/>
<br />

<h3>Configure osTicket Files and Permissions</h3>

<p>
Navigate to:
</p>

<p>
<strong>C:\inetpub\wwwroot\osTicket\include</strong>
</p>

<p>
Rename:
</p>

<p>
<strong>ost-sampleconfig.php</strong> → <strong>ost-config.php</strong>
</p>
<img src="https://i.imgur.com/Da5koEi.png" width="100%" alt="IIS Test Page"/>
<p>
Right-click <strong>ost-config.php</strong> → Properties → Security → Advanced
</p>

<p>
Disable inheritance and select <strong>Remove all inherited permissions</strong>.
</p>

<p>
Add a new permission:
</p>

<p>
<strong>Principal:</strong> Everyone<br />
<strong>Permissions:</strong> Full Control
</p>
<img src="https://i.imgur.com/gW6sLi4.png" width="100%" alt="IIS Test Page"/>
<br />

<h3>Database Setup with HeidiSQL</h3>

<p>
Install <strong>HeidiSQL</strong> and launch the application.
</p>

<p>
Create a new session using:
</p>

<p>
<strong>Username:</strong> root<br />
<strong>Password:</strong> root
</p>
<img src="https://i.imgur.com/ejdBAOn.png" width="100%" alt="IIS Test Page"/>
<p>
Connect to the server, right-click the unnamed database, and create a new database named:
</p>

<p>
<strong>osTicket</strong>
</p>

<br />

<h3>Finalize osTicket Installation</h3>
<img src="https://i.imgur.com/JzEOFaL.png" width="100%" alt="IIS Test Page"/>
<img src="https://i.imgur.com/qPiWdVy.png" width="100%" alt="IIS Test Page"/>
<p>
Return to the osTicket setup page in your browser.
</p>

<p>
Enter the database information and complete the installation.
</p>

<p>
After installation, log in at:
</p>

<p>
<strong>http://localhost/osTicket/scp/login.php</strong>
</p>
<br />

<h3>Post-Installation Cleanup</h3>

<p>
Delete the setup directory:
</p>

<p>
<strong>C:\inetpub\wwwroot\osTicket\setup</strong>
</p>

<p>
Set permissions on the following file to <strong>Read-only</strong>:
</p>

<p>
<strong>C:\inetpub\wwwroot\osTicket\include\ost-config.php</strong>
</p>

<p>
<strong>osTicket is now successfully installed and secured.</strong>
</p>
