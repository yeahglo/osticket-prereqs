<!-- os prereqs placeholder

<p align="center">

</p>

<h1>osTicket - Prerequisites and Installation</h1>
This is a walkthrough of the installation and set up for the open-source ticketing software, osTicket. You can use this walkthrough to follow along and even try it for yourself!<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)


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
- Download and install PHP Manager for IIS (look out 
- Install Rewrite Module
- Create C:\PHP directory by going to C: Drive > Right click > New > Folder > name it "PHP"
- Download PHP 7.3.8 files (be on the look for any extra prompts) > Right click > Extract All > Browse to the "PHP" folder > Extract
- Download and install VC Redistributable 

<p>
<img width="935" alt="Screen Shot 2023-06-26 at 4 54 13 PM" src="https://github.com/yeahglo/osticket-prereqs/assets/91516100/0da5b2b3-1750-4f49-8c4c-69e371bfff67">
</p>
-->
