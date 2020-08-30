---
title: "Setup Wordpress on MacOS"
date: 2020-08-30T12:15:05+08:00
tags: ["Guide"]
draft: false
---

### Install Wordpress and database setup

- Download and install [XAMPP](https://www.apachefriends.org/index.html)
- Create database in phpMyAdmin
- Download [Wordpress](https://wordpress.org/)
- Update **wp-config-sample.php** in **/wordpress/wp-config-sample.php** path
- Locate this line **define ('DB_NAME', 'database_name')**, replace the database_name with the name you used in step 4
- Update database username and password
- **define('DB_USER', 'root')**
- **define('DB_PASSWORD', '')**
- Move the wordpress folder to **htdocs**, you can rename the folder as well
- Navigate to **http://localhost/folder_name/wp-admin**, and start the installation

### Issues and tips

#### XAMPP MySQL Database cannot start

- ports is been used by other applications
- open XAMPP directory
- navigate to **my.cnf** in path **/Applications/XAMPP/xamppfiles/etc**
- change port from **3306** to **3307**
- add **innodb_force_recovery=1** under **myisam_sort_buffer_size=8M**
- restart Mysql with the command 
- **sudo /Applications/XAMPP/xamppfiles/bin/mysql.server start**
- [reference](https://stackoverflow.com/questions/27835348/mysql-database-cannot-start-on-xampp-for-mac/28358687#:~:text=cnf%22%20file%20and%20open%20it,or%20other%20apps%20%235.&text=Restart%20Mysql%20Server%20By%20Your,message%20%22Starting%20MySQL%20SUCCESS!%20%22)


#### Install theme and plugins

- update **wp-config.php**
- set files permission
- add **define('FS_METHOD', 'direct')** in **wp-config.php**
- [reference](https://wordpress.stackexchange.com/questions/19649/wordpress-on-localhost-lamp-doesnt-let-me-install-plugins#:~:text=For%20localhost%2C%20you%20can%20bypass,keep%20them%20in%20their%20folders.)


#### Changing permalinks not working
- check if **.htaccess** is writable (locate in project root directory)
- manually create if it's not exists yet
- [reference](https://wordpress.org/support/article/using-permalinks/)