<!--<h1>osTicket - Prerequisites and Installation</h1>
This is a walkthrough of the installation and set up for the open-source ticketing software, osTicket. You can use this walkthrough to follow along and even try it for yourself.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure
- Microsoft Remote Desktop
- Internet Information Services (IIS)
- PHP 7.3.8 & MySQL

<h2>Operating Systems Used </h2>

- Windows 10, version 22H2

<h2>List of Prerequisites</h2>

- Microsoft Azure Virtual Machine
- osTicket Installation Files
- Heidi SQL

<h2>Installation Steps</h2>

**Step 1: Create the VM within Microsoft Azure:**
- Create a resource group called "RG-osTicket"
- Create a VM called "vm-osticket" (Use Windows 10 Pro, version 22H2 - x64 Gen2 and Standard_D4s_v3 - 4cpus, 16 GiB memory)
- Make sure it auto populates to "RG-osTicket" for its resource group before the Review and Create step
- Note the username and password you're creating for Windows 10
- Make sure to checkmark the bottom part about licensing so you don't run into any issues (see 2nd image below)
</br>

<img width="812" alt="Screen Shot 2023-06-25 at 12 16 22 PM" src="https://github.com/yeahglo/osticket-prereqs/assets/91516100/c17f13b1-04be-4c8d-ba37-f9db0340b4db"></p>
<p>
<img width="691" alt="Screen Shot 2023-06-25 at 12 17 41 PM" src="https://github.com/yeahglo/osticket-prereqs/assets/91516100/ba93e774-64a3-4ae4-925f-bf393ad5af53"></p>


**Step 2: Log into the VM via RDP:**
- Copy the Public IP Address from the VM (Virutal Machines > "vm-osticket" > copy Public IP address)
- Log in, using your Windows 10 username and password
</br>

<p>
<img width="835" alt="Screen Shot 2023-06-25 at 12 21 31 PM" src="https://github.com/yeahglo/osticket-prereqs/assets/91516100/16904f4f-b371-4903-9719-703e74ffea4c">
</p>

**Step 3: Enable Internet Information Services (IIS)**
- Open IIS from the start menu (Right click start menu > Run > type in "control" > Programs > Programs and Features > Turn Windows Features on or off
- Under IIS > make sure Web Management Tools is enabled
- Under IIS > World Wide Web Services > Application Development Features, turn on CGI
- Under IIS > World Wide Web Services > Common HTTP Features, turn on all of the options here
- Click OK and allow it to install
</br>

<p>
<img width="778" alt="Screen Shot 2023-06-25 at 12 24 54 PM" src="https://github.com/yeahglo/osticket-prereqs/assets/91516100/650ba206-1435-4cbd-87a7-5622e959a694">
</p>


<p>
<img width="746" alt="Screen Shot 2023-06-25 at 12 26 53 PM" src="https://github.com/yeahglo/osticket-prereqs/assets/91516100/4834477e-e41c-47c8-bfd2-7356fa3a7d8b">
</p>

**Step 4: Test IIS:**
- Open a web broswer tab and type in "127.0.0.1"
- To ensure IIS enabled, you should see something similar to the browser on the right, below
</br>

<p>
<img width="797" alt="Screen Shot 2023-06-26 at 10 03 05 PM" src="https://github.com/yeahglo/osticket-prereqs/assets/91516100/3ad1c78e-d865-4149-a072-accd8a18f869">
</p>

**Step 5: Install the Requirements**
- Make sure to override any additional security prompts if you see them
- Download and install PHP Manager for IIS
- Install Rewrite Module
- Create C:\PHP directory by going to C: Drive > Right click > New > Folder > name it "PHP"
- Download PHP 7.3.8 files (be on the look for any extra prompts) > Right click > Extract All > Browse to the "PHP" folder > Extract
- Download and install VC Redistributable

<p>
<img width="935" alt="Screen Shot 2023-06-26 at 4 54 13 PM" src="https://github.com/yeahglo/osticket-prereqs/assets/91516100/0da5b2b3-1750-4f49-8c4c-69e371bfff67">
</p>

**Step 6: Install and Configure MySQL**
- Download and install MySQL 5.5.62
- Choose "Typical" installation
- Make sure to launch the Configuration Wizard
- Choose a "Standard Configuration"
- Use a simple password such as "Password1" _(Note: Always choose strong passwords in actual production)_

<p>
<img width="500" alt="Screen Shot 2023-06-25 at 12 42 16 PM" src="https://github.com/yeahglo/osticket-prereqs/assets/91516100/d5432980-7d50-4df6-b88e-7f7b1693df2a">
</p>

**Step 7: Make Changes in the IIS Admin Panel**
- Search for IIS > Right click it to run it as admin
- At the "vm-osticket" level, open the PHP Manager > Select a principal > browse to and open the php.cgi file
- At rhe "vm-osticket" level, restart the server from the right sidebar menu


<p>
<img width="1039" alt="Screen Shot 2023-06-25 at 12 45 47 PM" src="https://github.com/yeahglo/osticket-prereqs/assets/91516100/01d2b90c-94cc-4d71-84fb-3925afb9ca70">
</p>

**Step 8: Install osTicket Files and Set Up Installer**
- Download osTicket files
- Open a 2nd file explorer window, navigate to C: > inetpub > wwwroot
- Drag the "Upload" folder from the osTicket files to wwwroot to copy files over
- Rename the file, from "Upload" to "osTicket"
- At rhe "vm-osticket" level in the admin for IIS, restart the server from the right sidebar menu again
- Navigate to Sites > Default > osTicket
- From the right sidebar, click "Browse *:80"

_Note: At this point, osTicket Installer should be open in the browser. If it's not, there may be an error in the setup._

**Step 9: Enabling PHP Extensions and Configuring File Permissions**
- Navigate back Sites > Default > osTicket in the admin IIS panel
- Open PHP Manager at this level and scroll down to click "Enable or disable an extension"
- Enable the following 3 extensions: php_imap.dll, php_intl.dll, and php.opcache.dll
- Refresh the osTicket Installer in your browser (you should see more checkmarks where it lists the extensions)
- Navigate to your C: Drive > inetpub > wwwroot > osTicket > Include > ost-sampleconfig.php
- Remove the "sample" part of the name, so that it reads "ost-config.php"
- Right click on the folder > Advanced > Disable Inheritance > Remove All
- Set New Permissions > Everyone (click "Check Names" to populate) > Check All permissions and apply them

**Step 10: Continue Setting Up in the Browser**
- Click Continue
- Fill out each part of the form - choose a name, default email, and user information

**Step 11: Instal HeidiSQL**
- Download and open Heidi SQL
- Username will be "root", Password will be "Password1" _(Note: Never do this in actual production.)_
- Create a new session connection 
- Open a connection and right click to create a database called "osTicket"

**Step 12: Finish Setup in the Broswer**
- MySQL DB: osTicket
- MySQL user/password: root/Password1
- Click Install Now

_Note: If it's installed correctly, you should now see a Congratulations page telling you so. Make sure you copy all the links at the bottom of this page so that you know where to login and find documentation._-->
