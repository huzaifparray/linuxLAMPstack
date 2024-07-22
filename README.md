# Setting Up a LAMP Stack on Ubuntu
This guide will walk you through setting up a LAMP (Linux, Apache, MySQL/MariaDB, PHP) stack on an Ubuntu Virtual Machine (VM).
## Step 1:Update the package index on your Ubuntu VM:
sudo apt update
## Step 2: install apache server
sudo apt install apache2 -y
##Step 3: verify apache status
sudo systemctl status apache2
##Step 4: install mysql
sudo apt install mysql-server -y
##Step 5: secure mysql installation
sudo mysql_secure_installation
##Step 6: install php and required modules
sudo apt install php libapache2-mod-php php-mysql -y
##Step 7: adjust apache configuration
sudo nano /etc/apache2/mods-enabled/dir.conf   adjust to -<IfModule mod_dir.c>
    DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm
</IfModule>
##Step 8:restart apache
sudo systemctl restart apache2
##Step 9:Create a PHP info file to test PHP:
echo "<?php phpinfo(); ?>" | sudo tee /var/www/html/info.php
##Step 10:Access http://your_server_ip/info.php to verify PHP is working.
##Step 11: if you want a web interface to manage your Mysql you can install phpmyadmin
sudo apt install phpmyadmin -y
##Step 12 :Enable phpmyadmin configuration in Apache.
sudo phpenmod msqli
sudo systemctl restart apache2
##Step 13 :now we can access phpmyadmin at "https://your_server_ip/phpmyadmin"

