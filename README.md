# LampStack-Implementation
PROJECT 1- LAMP STACK IMPLEMENTATIONS
A “LAMP” stack is a group of open-source software that is typically installed together to enable a server to host dynamic websites and web apps.

Prerequisites
Launch an EC2 instance:

Go to the AWS Management Console and navigate to the EC2 service.
Click on "Launch Instance" and select the Ubuntu Server 20.04 LTS (or the latest version) AMI.
Choose an instance type, configure other settings as needed, such as security Group(which is a virtual firewall) and launch the instance.

Connect to the EC2 instance:

Once the instance is running, select it in the EC2 dashboard and click on "Connect".
Follow the instructions to connect using SSH. For example, using the terminal on your local machine:

ssh -i <path_to_key_file.pem> ubuntu@<public_dns_name>
Replace <path_to_key_file.pem> with the path to your private key file, and <public_dns_name> with the public DNS name of your EC2 instance.
Update the system packages:

sudo apt update

sudo apt upgrade

Install Apache:

sudo apt install apache2

Start Apache and enable it to start on boot:

sudo systemctl start apache2
sudo systemctl enable apache2
Verify Apache is running:

Open a web browser and enter your EC2 instance's public IP or public DNS in the address bar.
You should see the default Apache web page indicating a successful installation.

Install MySQL:
sudo apt install mysql-server

Secure the MySQL installation:

sudo mysql_secure_installation
Follow the prompts to set a root password and answer the security-related questions.

Install PHP:
sudo apt install php libapache2-mod-php php-mysql

Configure Apache to use PHP:

sudo nano /etc/apache2/mods-enabled/dir.conf
Move the index.php file before index.html in the DirectoryIndex line, like this:

DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm
Restart Apache for the changes to take effect:

sudo systemctl restart apache2
Test PHP:
Create a PHP info file in the web root directory:![EndResult](https://github.com/HassanSesay/LampStack-Implementation/assets/114838820/193222ca-d874-46bd-a9f5-93fe263817c0)

echo "<?php phpinfo(); ?>" | sudo tee /var/www/html/phpinfo.php
Open a web browser and navigate to http://<public_ip>/phpinfo.php. You should see the PHP information page.
