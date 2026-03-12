# osTicket: Prerequisites and Installation

![osTicket Logo](https://i.imgur.com/Clzj7Xs.png)

This lab documents the prerequisites and installation steps for setting up the open-source help desk ticketing system **osTicket** on a Windows 10 virtual machine hosted in Microsoft Azure.

---

## Environments and Technologies Used

- Microsoft Azure (Virtual Machines)
- Remote Desktop Protocol (RDP)
- Internet Information Services (IIS)
- PHP 7.3.8
- MySQL 5.5.62
- osTicket v1.15.8

## Operating System Used

- Windows 10 (21H2)

---

## Prerequisites

Before installing osTicket, the following components must be installed and configured:

- IIS (Internet Information Services) with CGI enabled
- PHP Manager for IIS
- URL Rewrite Module for IIS
- PHP 7.3.8
- Microsoft Visual C++ Redistributable
- MySQL 5.5.62
- HeidiSQL (for database management)

---

## Installation Steps

### Step 1: Create the Azure Virtual Machine

Create a Windows 10 VM in Azure with at least 2 vCPUs. Once deployed, connect to it using Remote Desktop (RDP) with the public IP address.

### Step 2: Enable IIS with CGI

Open **Control Panel > Programs > Turn Windows Features On or Off**.

Enable:
- Internet Information Services
- World Wide Web Services → Application Development Features → **CGI**

This allows IIS to process PHP files needed by osTicket.

### Step 3: Install PHP Manager and Rewrite Module

Download and install:
- **PHP Manager for IIS** (`PHPManagerForIIS_V1.5.0.msi`)
- **URL Rewrite Module** (`rewrite_amd64_en-US.msi`)

These allow IIS to understand PHP and handle URL routing properly.

### Step 4: Install PHP 7.3.8

Create the directory `C:\PHP`, then download and extract **PHP 7.3.8** (`php-7.3.8-nts-Win32-VC15-x86.zip`) into that folder.

In IIS Manager, use PHP Manager to register PHP by pointing to `C:\PHP\php-cgi.exe`.

### Step 5: Install Microsoft Visual C++ Redistributable

Install `VC_redist.x86.exe`. This is a required dependency for PHP to run on Windows.

### Step 6: Install MySQL 5.5.62

Install MySQL with the following settings:
- Setup Type: **Typical**
- Launch Configuration Wizard after install: **Yes**
- Configuration Type: **Standard**
- Set a root password (save this — you'll need it later)

### Step 7: Download and Set Up osTicket

1. Download osTicket v1.15.8
2. Extract the **upload** folder and copy it to `C:\inetpub\wwwroot`
3. Rename the folder from `upload` to `osTicket`
4. Reload IIS (stop and start the server)

### Step 8: Enable Required PHP Extensions

In IIS Manager, navigate to:
**Sites → Default → osTicket**, then open PHP Manager and enable the following extensions:
- `php_imap.dll`
- `php_intl.dll`
- `php_opcache.dll`

Refresh the osTicket browser page — more features will now show as enabled.

### Step 9: Configure ost-config.php

Navigate to `C:\inetpub\wwwroot\osTicket\include\`.

Rename `ost-sampleconfig.php` → `ost-config.php`

Right-click → Properties → Security → Disable inheritance → Remove all existing permissions → Add **Everyone** with **Full Control** (temporary, for setup).

### Step 10: Set Up the Database with HeidiSQL

Install **HeidiSQL**, open it, and create a new session using the MySQL root credentials. Then create a new database called `osTicket`.

### Step 11: Complete the osTicket Browser Setup

In your browser, navigate to `http://localhost/osTicket` and fill in:
- Help Desk Name
- Default email
- Admin username and password
- MySQL Database: `osTicket`
- MySQL Username: `root`
- MySQL Password: *(your root password)*

Click **Install Now!**

### Step 12: Clean Up

After installation:
- Delete `C:\inetpub\wwwroot\osTicket\setup`
- Set `ost-config.php` permissions back to **Read Only**

---

## Result

osTicket is now installed and accessible at:
- **End User Portal:** `http://localhost/osTicket`
- **Admin/Staff Panel:** `http://localhost/osTicket/scp/login.php`

---

*Next: [osTicket: Post-Installation Configuration](https://github.com/kentryan0/post-install-config)*
