
:octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: 
:octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: 

 **Name**: M.K.P.Tharanganie
 
 **SLIIT ID**:IT12084432
 
 **Practical Session**: WE Thursday (7/30/2015)
 
 **Practical Number**: Lab 5

#Download and install ownCloud on your own Linux server

1. **Create sentOS Linux server**

![sentOS](http://i57.tinypic.com/38pit.jpg)

![sentOS](http://i59.tinypic.com/2m5frit.jpg)

![sentOS](http://i60.tinypic.com/zkrhbk.jpg)

![sentOS](http://i60.tinypic.com/1zoj5ut.jpg)

![sentOS](http://i57.tinypic.com/2usfm1y.jpg)

![sentOS](http://i61.tinypic.com/29za246.jpg)

![sentOS](http://i62.tinypic.com/2w2r82d.jpg)

![sentOS](http://i62.tinypic.com/hwxqb6.jpg)

![sentOS](http://i59.tinypic.com/6zqwdg.jpg)

![sentOS](http://i60.tinypic.com/sy6xkx.jpg)

![sentOS](http://i62.tinypic.com/14e5rf4.jpg)

![sentOS](http://i61.tinypic.com/312k77p.jpg)

![sentOS](http://i60.tinypic.com/vzbfo4.jpg)

![sentOS](http://i57.tinypic.com/4goysz.jpg)

![sentOS](http://i58.tinypic.com/2ptdlwm.jpg)

![sentOS](http://i57.tinypic.com/kbvbsm.jpg)

![owncloud](http://i62.tinypic.com/317iffb.jpg)

![owncloud](http://i62.tinypic.com/2dha9sh.jpg)

![owncloud](http://i60.tinypic.com/dfu0yr.jpg)

![owncloud](http://i61.tinypic.com/29ashl4.jpg)

![owncloud](http://i60.tinypic.com/jsll41.jpg)

![owncloud](http://i61.tinypic.com/9s4e3d.jpg)

![owncloud](http://i59.tinypic.com/t4z1au.jpg)

![owncloud](http://i62.tinypic.com/23gxxfc.jpg)

![owncloud](http://i58.tinypic.com/91kjdx.jpg)


2. **Installation of ownCloud in Linux** (http://www.itzgeek.com/how-tos/linux/centos-how-tos/install-owncloud-7-on-centos-7-rhel-7.html#axzz3hYXBLvvc)

* install PHP, Apache web server and MySQL server on CentOS 7. For demo purpose i installed both SQLite and MySQL on CentOS

**cmd:**

yum install httpd php php-mysql mariadb-server mariadb sqlite php-dom php-mbstring php-gd php-pdo wget

![installation of owncloud](http://i62.tinypic.com/2vacqyb.jpg)

![installation of owncloud](http://i58.tinypic.com/5cy5hy.jpg)

![installation of owncloud](http://i60.tinypic.com/2nb6rec.jpg)

![installation of owncloud](http://i60.tinypic.com/2bd0mt.jpg)


* Set SELinux to allow OwnCloud to write the data.

**cmd:**

setsebool -P httpd_unified 1

* Allow apache in firewall.

**cmd:**

firewall-cmd --permanent --zone=public --add-service=http
firewall-cmd --permanent --zone=public --add-service=https
firewall-cmd --reload

![installation of owncloud](http://i61.tinypic.com/ir803s.jpg)

* Start Apache and MariaDB.

**cmd:**

systemctl start httpd.service
systemctl start mariadb.service

* Auto start the service at system start-up.

**cmd:**

systemctl enable httpd.service
systemctl enable mariadb.service

![installation of owncloud](http://i62.tinypic.com/zukpie.jpg)


#Download and Setup:

* Download ownCloud from official website or enter the fallowing command on terminal.

**cmd:**

wget https://download.owncloud.org/community/owncloud-8.1.0.tar.bz2

![installation of owncloud](http://i59.tinypic.com/2qxssg7.jpg)

* Extract the archive.

**cmd:**

tar -jxvf owncloud-7.0.0.tar.bz2 -C /var/www/html/

67
![installation of owncloud]()

Allow the web server to read and write the files on cloud directory.
cmd
chown -R apache.apache /var/www/html/owncloud/

68
![installation of owncloud]()

#Create Database:
If you are setting up a MariaDB for the first time, here is the tutorial on Securing MariaDB.  MariaDB server must be started before creating the database, login to MySQL server.
cmd
mysql -u root -p

69
![installation of owncloud]()

Create database called “clouddb”
cmd
create database clouddb;

70
![installation of owncloud]()

Allow “clouddbuser” to access the “clouddb” database on localhost with predefined password.
cmd
grant all on clouddb.* to 'clouddbuser'@'localhost' identified by 'password';

71
![installation of owncloud]()

#Configure Apache server:
cmd
vi /etc/httpd/conf.d/owncloud.conf

Add the following.system

<IfModule mod_alias.c>
Alias /owncloud /var/www/html/owncloud
</IfModule>
<Directory “/var/www/html/owncloud”>
Options Indexes FollowSymLinks
AllowOverride All
Order allow,deny
allow from all
</Directory>


Remember to restart all services related to Apache server.
cmd
systemctl restart httpd.service




**Configure ownCloud:**
Open up web browser, point a URL to http://your-ip-address/owncloud ( http://Your-custom-domain). Browser will automatically take you to ownCloud setup page where it must be configured before going to live. Enter admin user name, password, data folder location and database details. You can choose any one of the database from SQLite or MySQL. If you choose SQLite database, you do not require to enter database details. where as MySQL database requires database user, password and data base name.

![installation of owncloud]()
![installation of owncloud]()
![installation of owncloud]()
![installation of owncloud]()





:octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: 
:octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: :octocat: 


