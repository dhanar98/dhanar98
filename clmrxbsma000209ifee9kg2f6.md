---
title: "Install Phalcon Framework And PHP-Nginx Using Bash Script - UBUNTU"
datePublished: Wed Sep 20 2023 15:53:41 GMT+0000 (Coordinated Universal Time)
cuid: clmrxbsma000209ifee9kg2f6
slug: install-phalcon-framework-and-php-nginx-using-bash-script-ubuntu
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/9WnjxT1NCoY/upload/ab1ecb111a0f1a790d9bd766ba185a26.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1695225211121/72749f19-baf0-4628-b6fd-8d00927619f7.png
tags: phalcon, php7, bash-script

---

## **Unlocking Web Performance: Installing Phalcon Framework and PHP-Nginx with a Bash Script on Ubuntu**

In today's fast-paced digital landscape, a website's speed and performance are paramount to its success. Slow-loading websites not only frustrate visitors but also receive lower rankings in search engine results.

To address these critical factors, developers often turn to specialized web frameworks and server configurations. One powerful combination for boosting website performance is the Phalcon framework and PHP-Nginx on an Ubuntu server, made even more accessible through a Bash script.

In this article, we will take you through the process of installing Phalcon Framework and PHP-Nginx using a Bash script on your Ubuntu server. This Single File Execution helps you Create the Setup for PHP-NGINX, Phalcon Framework Installation.

### **Why Phalcon and PHP-Nginx?**

Before diving into the installation process, it's essential to understand why Phalcon Framework and PHP-Nginx are the dynamic duos you need to supercharge your website.

#### **Install PHP-NGINX :**

Nginx is a popular web server known for its speed and reliability. When combined with PHP-FPM (FastCGI Process Manager), it becomes PHP-Nginx – a powerful setup for serving PHP-based websites. PHP-Nginx is known for its ability to handle a high volume of concurrent requests without slowing down, making it ideal for websites that prioritize performance.

**Step 1: Update and Upgrade**

The first step is to ensure that your system is updated and all existing packages are upgraded. We accomplish this with the following commands:

```bash
# Update package list and upgrade existing packages
sudo apt update && sudo apt upgrade -y
```

This ensures that your system is running the latest software updates.

**Step 2: Installing Nginx**

Nginx is a high-performance web server that can also serve as a reverse proxy. We can install it with the following command:

```bash
sudo apt install nginx -y
```

Once installed, you can check the status of Nginx with:

```bash
sudo systemctl status nginx
```

**Step 3: Installing Curl**

Curl is a versatile command-line tool for making HTTP requests. We can install it using:

```bash
sudo apt install curl
```

**Step 4: PHP Installation**

Now, let's install PHP 7.4 and the required modules for web development. We start by adding the PHP repository:

```bash
sudo apt install software-properties-common
sudo add-apt-repository ppa:ondrej/php
sudo apt update
```

Then, we can install PHP 7.4 and additional modules:

```bash
sudo apt install -y php7.4 php7.4-curl php7.4-gd php7.4-json php7.4-mbstring php7.4-zip php7.4-fpm php7.4-cli php7.4-dev 

sudo apt install libpcre3-dev php7.4-xml php7.4-mysql php7.4-imagick php7.4-mysql php7.4-pgsql  php7.4-psr

echo "PHP 7.4 INSTLATTION WITH MODULES - SUCCESSFULL"
```

#### **Install Phalcon Framework**

**Step 1: Install GCC**

GCC is the GNU Compiler Collection, and Curl is a tool for making HTTP requests. We need them for compiling and downloading Phalcon. Install them using the following commands:

```bash
sudo apt install gcc
```

**Step 2: Add Phalcon Repository**

We will use the Phalcon repository to install the framework. Run the following command to add the Phalcon repository:

```bash
curl -s https://packagecloud.io/install/repositories/phalcon/stable/script.deb.sh | sudo bash
```

**Step 3: Download Phalcon**

Navigate to the temporary directory and download the Phalcon source code from GitHub:

```bash
cd /tmp
curl -sLO https://github.com/phalcon/cphalcon/archive/refs/tags/v4.1.2.zip
```

**Step 4: Unzip and Build Phalcon**

```bash
unzip v4.1.2.zip
cd cphalcon-4.1.2/build
```

Now, run the installation script to build and install Phalcon:

```bash
./install
```

**Step 5: Clean Up (Optional)**

If you want to free up disk space, you can remove the downloaded files:

```bash
rm /tmp/v4.1.2.zip
rm -r /tmp/cphalcon-4.1.2
echo "PHALCON COMPILATION AND INSTALLATION SUCCESSFULL"
```

#### Setup Configuration in Nginx and PHP Phalcon For Phalcon Project

**Step 1: Installing Phalcon**

Phalcon is a PHP extension that enhances the performance of web applications. We will start by configuring Phalcon on your system. Here are the steps:

```bash
# Create Phalcon configuration files
echo "extension=phalcon.so" | sudo tee /etc/php/php7.4/fpm/conf.d/30-phalcon.ini
echo "extension=phalcon.so" | sudo tee /etc/php/php7.4/cli/conf.d/30-phalcon.ini
echo "extension=phalcon.so" | sudo tee /etc/php/7.4/mods-available/phalcon.ini

# Create symbolic links for Phalcon configuration
sudo ln -s /etc/php/7.4/mods-available/phalcon.ini /etc/php/7.4/fpm/conf.d/30-phalcon.ini
sudo ln -s /etc/php/7.4/mods-available/phalcon.ini /etc/php/7.4/cli/conf.d/30-phalcon.ini
echo "PHALCON SYMLINK CREATION SUCCESSFULL FOR PHP.INI"
```

**Step 2: Configuring Nginx For the Phalcon Project**

Nginx is a powerful web server that we will use to serve our Phalcon application. Here's how to set up the Nginx configuration:

```bash
# Create the Nginx configuration file for Phalcon
sudo bash -c 'cat > /etc/nginx/sites-available/phalcon-pro.conf <<EOF
server {
    listen 80;
    server_name localhost;
    root /var/www/phalcon/public; 
    index index.php;
    charset utf-8;
    location / {
        try_files \$uri \$uri/ /index.php?\_url=\$uri&\$args;
    }
    location ~ \.php {
        fastcgi_pass unix:/run/php/php7.4-fpm.sock;
        fastcgi_index /index.php;
        include fastcgi_params;
        fastcgi_split_path_info ^(.+\.php)(/.+)$;
        fastcgi_param PATH_INFO \$fastcgi_path_info;
        fastcgi_param PATH_TRANSLATED \$document_root\$fastcgi_path_info;
        fastcgi_param SCRIPT_FILENAME \$document_root\$fastcgi_script_name;
    }
    location ~ /\.ht {
        deny all;
    }
}
EOF'

# Create a symbolic link to enable the Nginx site
sudo ln -s /etc/nginx/sites-available/phalcon-pro.conf /etc/nginx/sites-enabled/
```

**Step 3: Starting Services**

Let's start and enable Nginx and PHP-FPM to apply the changes:

```bash
# Start and enable Nginx and PHP-FPM
sudo systemctl start nginx
sudo systemctl enable nginx
sudo systemctl start php7.4-fpm
sudo systemctl enable php7.4-fpm
```

**Step 4: Testing**

To ensure everything is working correctly, run the following commands:

```bash
# Test Nginx configuration and reload Nginx
sudo nginx -t
sudo systemctl reload nginx

echo "PHP and Nginx installation complete."
#Check Phalcon is installed or not
php -m | grep phalcon

echo "REMINDER : CHANGE ROOT PATH IN NGINX CONF"
```

### **SYSTEM INFORMATION**

* **OS SYSTEM: UBUNTU**
    
* **PHALCON VERSION: 4.1.2**
    
* **PHP VERSION: 7.4**
    

To Simplify this work execute all the commands in a single command copy and paste the content save the file with .sh extension into your system and execute this command.

%[https://gist.github.com/dhanar98/45b3ed3f8cc3227a2f3dd2de05d0ebff] 

```bash
bash script_filename.sh
```

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