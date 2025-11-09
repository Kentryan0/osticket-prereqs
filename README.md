# osticket-prereqs
<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com/watch?v=k_CDukV-bcs)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Windows Server or Linux environment
- Basic knowledge of web servers (IIS or Apache)
- Access to administrator/root privileges
- Understanding of file permissions and networking basics
  

<h2>Installation Steps</h2>

<p>
<img width="2208" height="1436" alt="image" src="https://github.com/user-attachments/assets/f043cd69-7335-4d4f-b574-cc6c70ec0c48" />

</p>
<p>
Create an Azure Virtual Machine Windows 10 Sign in to the Azure Portal → https://portal.azure.com

Go to Create a Resource → Virtual Machine

Choose:

Image: Windows Server 2019 or 2022 Datacenter

Size: At least 2 vCPUs and 4GB RAM

Inbound Ports: Allow RDP (3389) and HTTP (80)

Set username and password, then Create the VM.
</p>
<br />

<p>
  Connect to the VM

Once deployed, go to your VM’s overview in Azure.

Click Connect → RDP, download the RDP file, and log in using your credentials.
<p>

</p>
<p>
Install IIS, PHP, and MySQL
</p>
<br />

<p>

</p>
<p>
Download and extracted osTicket to C:\inetpub\wwwroot.

Configure IIS to serve the site and set PHP as a handler.

Create a MySQL database and linked it during setup.

Complete the web-based installer and secured the installation.
</p>
<br />
