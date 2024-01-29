---
title: "How To Install Phalcon PHP On XAMPP For Windows 11"
seoTitle: "2023 - Install Phalcon on XAMPP For Windows 11"
seoDescription: "Install Phalcon on Windows 11 XAMPP: Download XAMPP, select components, set directory, get Phalcon DLL, configure PHP.ini, create project"
datePublished: Sun Jul 30 2023 16:25:00 GMT+0000 (Coordinated Universal Time)
cuid: clkpnjrev000609mveol73t68
slug: how-to-install-phalcon-php-on-xampp-for-windows-11
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1706504532074/dc7694d3-74a7-4dbc-9c5c-2fde27e883b6.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1706504556070/17b36eee-f26d-4e47-9c46-957298d6ec03.png
tags: phalcon, php, xampp, 2articles1week, php8

---

# Install Phalcon PHP On XAMPP For Windows 11

In This article, We will go over the steps of Installing XAMPP and Phalcon on Your Windows 11 system. Before going to the setup we need to know about Phalcon Framework.

## What is Phalcon?

*Phalcon is an open-source full-stack framework for PHP, written as a C-extension. Phalcon is optimized for high performance. Its unique architecture allows the framework to always be memory resident, offering its functionality whenever it’s needed, without expensive file stats and file reads that traditional PHP frameworks employ.*

[![Phalcon-Documentation](https://img.shields.io/badge/Phalcon_Documentation-ffd200?style=for-the-badge&logo=falcon&logoColor=darkgreen align="left")](https://docs.phalcon.io/5.0/en/introduction)

[![Github-Repository](https://img.shields.io/badge/Phalcon_Github-ffd200?style=for-the-badge&logo=falcon&logoColor=darkgreen align="left")](https://github.com/phalcon/cphalcon)

### INSTALL XAMPP ON WINDOWS 11

\*\*Step 1: Download XAMPP on Official Site \*\*

XAMPP is an easy-to-install Apache distribution containing MariaDB, PHP, and Perl. Just download and start the installer. It's that easy.

[![XAMPP-Official](https://img.shields.io/badge/XAMPP_OFFICAL_Website-FB7A24.svg?style=for-the-badge&logo=XAMPP&logoColor=white align="left")](https://www.apachefriends.org/download.html)

Download XAMMP ⬇️

[![XAMPP-Download](https://img.shields.io/badge/XAMPP_Download-E6526F.svg?style=for-the-badge&logo=Apache-Flink&logoColor=white align="left")](https://sourceforge.net/projects/xampp/files/XAMPP%20Windows/8.1.17/xampp-windows-x64-8.1.17-0-VS16-installer.exe)

\*\*Step 2: Run the Installer \*\*

The Downloading will take a couple of minutes after that run the downloaded installer in your system.

![install-xampp-on-windows-11-run-the-installer](https://cdn.hashnode.com/res/hashnode/image/upload/v1690703506192/3c1bbbc6-6327-44f9-b726-f23229232659.png align="left")

**Step 3: Choose Components**

During the installation, you'll be prompted to select the components you want to install. By default, Apache, MySQL, PHP, and phpMyAdmin are selected. You can keep the default selection or choose additional components based on your requirements.

![setup-the-components-in-xampp-in-windows-11](https://cdn.hashnode.com/res/hashnode/image/upload/v1690703872911/d5b92978-0343-41c3-939c-fb6ee6562422.png align="center")

**Step 4: Installation Process**

* Choose the installation directory for XAMPP. The default directory is usually "C:\\xampp, but you can change it if needed.
    
    ![setup the xampp directory](https://cdn.hashnode.com/res/hashnode/image/upload/v1690707774085/be7a734e-c7d1-4ad2-8ada-b29113c14473.png align="center")
    
* Once you've selected the components and the installation directory, click the "Install" button to start the installation process. The setup will extract and install the selected components on your Windows 11 system.
    
* After clicking "Finish," the XAMPP Control Panel will open. From here, you can start and stop Apache, MySQL, and other installed components. Make sure Apache and MySQL are running by checking the status in the control panel.
    
    ![control apache and mysql using xampp](https://cdn.hashnode.com/res/hashnode/image/upload/v1690723343455/280ad098-9e12-445f-b803-dd32a41b3d36.png align="center")
    

### INSTALL PHALCON ON WINDOWS 11

To use Phalcon on Windows we need to download a DLL library. based on the xampp php version download the DLL library on phalcon GitHub release page.

\*\*Step 1: Download Phalcon DLL library \*\*

Find the Phalcon Library's Different versions releases in the below link ⬇️

[![download-phalcon-releases](https://img.shields.io/badge/phalcon-releases-ffd200.svg?style=for-the-badge&logo=falcon&logoColor=white align="left")](https://github.com/phalcon/cphalcon/releases)

Download Here ⬇️

[![download-phalcon-v5.0.1](https://img.shields.io/badge/phalcon-v5.0.1-ffd200?style=for-the-badge&logo=falcon&logoColor=darkgreen align="left")](https://github.com/phalcon/cphalcon/releases/download/v5.0.1/phalcon-php8.1-ts-windows2019-vs16-x64.zip)

* Extract the downloaded zip folder
    
* Cut the Phalcon DLL file and paste it into the below-mentioned path
    
* ```bash
          C:\xampp\php\ext
    ```
    

**Step 2: Configure PHP.ini File Load Phalcon library**

* Edit the php.ini File append at the end, and restart your webserver to load the extension.
    
* ```bash
          extension=php_phalcon.dll
    ```
    
* The PHP Info page shows this information
    
    ![phalcon-dll-configuration-in-xampp](https://cdn.hashnode.com/res/hashnode/image/upload/v1690725973002/fe3369fb-89ab-48b8-ba8e-ba754f24fea2.png align="center")
    

### SETUP PHALCON - PROJECT IN XAMPP

Download or Clone the Project from GitHub ⬇️

[![download-phalcon-project](https://img.shields.io/badge/phalcon_setup-181717.svg?style=for-the-badge&logo=GitHub&logoColor=white%22 align="left")](https://github.com/dhanar98/phalcon-skeleton-xampp)

* Run the Project From Below Path \*\* C:\\xampp\\htdocs \*\*
    
* Do The Instructions mentioned in the README. md File.
    
* Restart the server and The Magic ✨
    

![phalcon-xampp-skeleton](https://cdn.hashnode.com/res/hashnode/image/upload/v1690730870355/3a5b06fa-7b72-4a38-a5ff-de3e5f649835.png align="center")

<div data-node-type="callout">
<div data-node-type="callout-emoji">💻</div>
<div data-node-type="callout-text"><strong>System Information :</strong></div>
</div>

```plaintext
OS VERSION : WINDOWS 11
PHP VERSION : 8.1.17
PHALCON VERSION : 5.0.1
```

<div data-node-type="callout">
<div data-node-type="callout-emoji">🔗</div>
<div data-node-type="callout-text"><strong>Reference Links :</strong></div>
</div>

* [install-phalcon-framework-on-windows](https://phalcon.io/en-us/download/windows)
    
* [phalcon-vokuro-sample-application](https://github.com/niden/phalcon-vokuro/tree/master)
    

I hope this article is helpful to all of you. follow and support 💜💜💜💰

**Updated On Oct 10, 2023:**  
The last version of PHP 7, PHP 7.4, reached its end of life (EOL) on November 28, 2022. This means that PHP 7.4 will no longer receive security updates and could be exposed to unpatched security vulnerabilities. but it's time to embrace the future with PHP 8. The benefits in terms of performance, features, and security make it a worthwhile investment. Additionally, running the latest PHP version ensures that your web applications remain secure and up-to-date. Don't wait; start planning your migration to PHP 8 today.

<div data-node-type="callout">
<div data-node-type="callout-emoji">📱</div>
<div data-node-type="callout-text"><strong>Connect With Me:</strong></div>
</div>

<center>
[![Gmail](https://img.shields.io/badge/gmail-F44336?style=for-the-badge&logo=gmail&logoColor=white)](mailto:dhanasekarravi98@gmail.com)
[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/dhanar98/)
[![Instagram](https://img.shields.io/badge/instagram-000?style=for-the-badge&logo=instagram&logoColor=ffd200)](https://www.instagram.com/dhanar.98/)
[![Whatsapp](https://img.shields.io/badge/WhatsApp-25D366.svg?style=for-the-badge&logo=WhatsApp&logoColor=white)](https://wa.me/9025165942/?text=hi%20%2C%20ping%20you%20from%20via%20hashnode%20blog)
</center>