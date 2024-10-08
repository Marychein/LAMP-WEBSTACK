# LAMP-WEBSTACK
CREATING A LAMP WEBSTACK ON EC2 INSTANCE WITH UBUNTU SERVER
Lamp-Webstack
Setting up a LAMP Stack on an Amazon EC2 Instance
A stable and effective environment is critical in the field of web development. Several web applications and dynamic webpages have been built on the Linux, Apache, MySQL, and PHP (LAMP) stack. Let's explore the nuances of configuring a LAMP stack on an Amazon EC2 instance in this in-depth tutorial, giving you the ability to easily develop, launch, and host your web applications.

Understanding the Components
Before we dive into the setup process, let's briefly understand the components of the LAMP stack:

Linux: Ubuntu Server 22.04 LTS serves as our operating system.
Apache: Apache HTTP Server acts as the web server.
MySQL: MySQL Database Server manages our relational databases.
PHP: PHP, the Hypertext Preprocessor, handles server-side scripting.
Setting up the EC2 Instance
1. Launch an EC2 Instance
Sign in to the AWS Management Console.
Navigate to the EC2 Dashboard and click on "Launch Instance."
Select Ubuntu Server 22.04 LTS as the operating system.
2. Configure Instance Details
Customize the instance type, network, subnet, security group, and other settings according to your requirements.
3. Add Storage
Allocate storage space based on your application needs.
4. Add Tags
This can be optional
5. Configure Security Group
Establish a security group, allowing inbound traffic on ports:
80 (HTTP)
22 (SSH)
443 (HTTPS)
Make sure to limit SSH access to your IP address for security.
6. Review and Launch
Review your configuration and proceed with launching the instance.
7. Connect to the Instance
Use  ssh -i path/to/key pair ubuntu@public address
Installing the LAMP Stack
1. Update Package Repository
sudo apt update

3. Install Apache
sudo apt install apache2

4. Enable and Verify Apache
Enable Apache to start at boot: sudo systemctl enable apache2

Check the status of Apache to ensure it’s running: sudo systemctl status apache2

4. Test Apache Installation
Access Apache by visiting: http://54.165.94.198/ on your browser
Apache Installation History
1  ls
    2  cd /
    3  ls
    4  cd
    5  ls
    6  clear
    7  sudo apt update
    8  sudo apt install apache2
    9  sudo systemctl status apache2
   10  curl http://localhost:80
   11  curl http://54.165.94.198/
   12  history
   13  clear

6. Install MySQL
Install MySQL Server: sudo apt install mysql-server

Secure the MySQL installation: sudo mysql_secure_installation

sudo apt install mysql-server
   15  sudo mysql
   16  mysqul
   17  sudo mysql
   18  sudo mysql_secure_installation
   19  sudo msql -p
   20  sudo mysql -p
   21  ls
   22  history
   23  history | history.txt

6. Install PHP
Install PHP and necessary modules: sudo apt install php libapache2-mod-php php-mysql

Creating a Virtual Host with Apache
1. Set Up Domain Name
Create a directory for your project under /var/www/: sudo mkdir /var/www/projectlamb

change ownership sudo chown -R $USER:$USER /var/www/projectlamb

2. Configuration with Apache
Create a new virtual host configuration file in Apache's sites-available directory: sudo nano /etc/apache2/sites-available/projectlamb.conf

Add the following configuration:

<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    ServerName projectlamb
    ServerAlias www.projectlamb
    DocumentRoot /var/www/projectlamb
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
3. Enable Virtual Host
Enable your newly created virtual host: sudo a2ensite projectlamb

Disable the default Apache configuration: sudo a2dissite 000-default

4. Reload Apache
Ensure changes take effect: sudo systemctl reload apache2

5. Testing
Create an index.html file in your project directory:

echo "<h1>This is Marychein</h1>" > /var/www/projectlamb/index.html

Access the website via the browser at http://<public-ip-address>:80

Enabling PHP on the Website
1. Modify Directory Index
Adjust Apache’s configuration to prioritize PHP files:

sudo vi /etc/apache2/mods-enabled/dir.conf

Move index.php to the first position:

<IfModule mod_dir.c>
    DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm
</IfModule> 
2. Reload Apache
Apply the changes: sudo systemctl reload apache2

1  $ sudo apt install php libapache2-mod-php php-mysql
    2  php -v
    3  sudo mkdir /var/www/projectlamp
    4  sudo chown -R $USER:$USER /var/www/projectlamp
    5  sudo vi /etc/apache2/sites-available/projectlamp.conf
    6  sudo ls /etc/apache2/sites-available
    7  sudo a2ensite projectlamp
    8  sudo a2dissite 000-default
    9  sudo apache2ctl configtest
   10  sudo systemctl reload apache2
   11  sudo echo 'Hello LAMP from hostname' $(TOKEN=curl -X PUT "http://169.254.169.254/latest/api/token" -H "X-aws-ec2-metadata-token-ttl-seconds: 21600" && curl -H "X-aws-ec2-metadata-token: $TOKEN" -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(TOKEN=curl -X PUT "http://169.254.169.254/latest/api/token" -H "X-aws-ec2-metadata-token-ttl-seconds: 21600" && curl -H "X-aws-ec2-metadata-token: $TOKEN" -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectlamp/index.html
   12  sudo vim /etc/apache2/mods-enabled/dir.conf
   13  sudo systemctl reload apache2
   14  vim /var/www/projectlamp/index.php
   15  sudo rm /var/www/projectlamp/index.php
   16  history

3. Create PHP Test Script
Create a simple PHP script to verify the installation: echo "<?php phpinfo(); ?>" > /var/www/projectlamp/index.php

4. Test PHP Installation
Refresh your page and verify that PHP is working

Conclusion
My knowledge and understanding of web hosting and server management have been much enhanced by the invaluable hands-on experience of setting up a LAMP stack on an AWS EC2 instance. Having learned how to configure Linux, Apache, MySQL, and PHP from the ground up, I was able to develop scalable web applications with greater ease. This project offered a great platform for future work in DevOps and web development, as I can now set up stable infrastructures for dynamic websites.

These abilities will become increasingly important in the future for more complicated projects, especially in cloud environments where performance and scalability are crucial. I can't wait to use what I've learnt here in upcoming projects and keep honing my server infrastructure management skills.
