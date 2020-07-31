---
title: "Install Opencart locally on macOS"
date: 2020-06-14T17:42:43+08:00
tags: ["Guide"]
draft: false
---

### Install Opencart and run it locally on macOS Catalina

- Download and install [XAMPP](https://www.apachefriends.org/download.html)
- Download [Opencart](https://www.opencart.com/index.php?route=cms/download)
- Copy and paste **upload** folder from downloaded Opencart folder to XAMPP root directory **/Applications/XAMPP/htdocs**
- Navigate to **/upload** directory and rename **config-list.php** to **config.php**
- Repeat step above in **/upload/admin** directory
- Change **upload/system/library** and **upload/system/storage** folder permission to read and write
- Rename **upload** directory to your project name
- Launch XAMPP and navigate to **localhost/phpmyadmin** to create a database for Opencart
- Navigate to **localhost/your-project-name** and start the installation of Opencart



{{< rawhtml >}}
  <img class="ui fluid image" src="/img/opencart.png">  
{{< /rawhtml >}}