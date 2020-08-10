---
title: "Setup JDeveloper on macOS"
date: 2020-07-31T20:53:23+08:00
tags: ["Guide"]
draft: false
---

### JDK Setup

- Download and install [Oracle JDK](https://www.oracle.com/sg/java/technologies/javase/javase-jdk8-downloads.html) 
- Check your machine Java version **java -version**
- If there are more than one version of Java is available in your machine, you can set it to JAVA_HOME
- Java path in macOS 10.15.5 **/Library/Java/JavaVirtualMachines**, you can **ls** to check which version is available in your machine
- For the installation of JDeveloper, the Oracle JDK must be use 

{{< rawhtml >}}
  <img class="ui fluid image" src="/img/oracle_jdk8.png" style="width: auto">
{{< /rawhtml >}}

- export JAVA_HOME=/path/java_version/Contents/Home
- Replace path with the Java path mentioned above
- Replace the java_version with your installed Oracle JDK

### Install JDeveloper

- Download and install [JDeveloper 12C](https://www.oracle.com/tools/downloads/Jdeveloper-12c-downloads.html)
- There are two generic files that need to be download
- After the download is completed, navigate to the path where you downloaded the JDeveloper 
- Run this command **java -jar filename**, filename must be the first downloaded file

### Setup Oracle Database

- Download [Docker](https://docs.docker.com/docker-for-mac/install/)
- Register an ID and go to docker hub search for **Oracle Database Enterprise Edition**
- Follow the steps below to connect the Oracle database for the first time

{{< rawhtml >}}
  <p class="show-in-mobile">
    <a href="https://gist.github.com/luisychun/bbddabe73b4c955f7b5193b678baee23" target=_blank>Gist</a>
  </p>
{{< /rawhtml >}}

{{< rawhtml >}}<div class="hide-in-mobile">{{< /rawhtml >}}
```shell
docker login
docker run -d -it -p 1521:1521 --name oracle store/oracle/database-enterprise:12.2.0.1
docker exec -it oracle bash -c "source /home/oracle/.bashrc; sqlplus /nolog"
connect sys as sysdba; //Password: Oradoc_db1
alter session set"_ORACLE_SCRIPT"=true;
create user dummy identified by dummy;
GRANT ALL PRIVILEGES TO dummy;
```
{{< rawhtml >}}</div>{{< /rawhtml >}}

- Download [SQL Developer](https://www.oracle.com/sg/tools/downloads/sqldev-v192-downloads.html)
- Setup the connection as below

{{< rawhtml >}}
  <img class="ui fluid image" src="/img/sql_developer.png">
{{< /rawhtml >}}

### Docker related commands
- list all the containers
```shell
docker ps -a
```

- run container
```shell
docker container [name] start
```

- remove container
```shell
docker container rm [container id]
```

{{< rawhtml >}}
  <img class="ui fluid image" src="/img/docker-container.png">
{{< /rawhtml >}}