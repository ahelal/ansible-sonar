[![Build Status](https://travis-ci.org/ahelal/ansible-sonar.svg?branch=master)](https://travis-ci.org/ahelal/ansible-sonar)
#Readme

This ansible role deploys sonar for Ubuntu 12.04 (tested on vagrant)

##Prerequisite
* Having ansible installed on your workstation. 
* optional postgresql and mysql server
* java either JDK or JRE depanding if your going to use java based projects

##How to install
* Use github to clone/fork in your role directory
* ansible galaxy ```ansible-galaxy install adham.helal.sonar```

##Variables 
  Mostly you would need to configure JDBC setting if you need to tweak more have a look at the default variables are located **defaults/main.yml**. By default h2 database will be used. You can still setup mysql or postgresql in the JDBC setting. 
  To install postgres or mysql search ansible-galaxy you can use ```ansible-galaxy install Ansibles.mysql``` or ```ansible-galaxy install Ansibles.postgresql``` 

  - *sonar_jdbc_driver:*  You can use postgres, h2 or mysql

    ```sonar_jdbc_driver: "h2"```

  - *sonar_jdbc_host:* DB hostname

    ```sonar_jdbc_host : "127.0.0.1"```
  
  - *sonar_jdbc_port:* DB port

    ```sonar_jdbc_port : "9092"```
  
  - *sonar_jdbc_user:* DB username 

    ```sonar_jdbc_user : "sonar"```

  - *sonar_jdbc_pass:* DB password 

    ```sonar_jdbc_pass : "password"```

  - *sonar_jdbc_db:* DB name

    ```sonar_jdbc_pass : "sonardb"```


##Configure
You can configure your variables in ansible with one of the following

 * Create a variable in host/group variables directory. (recommended)
 * Editing var/main.yml
 * Run ansible-playbook with -e
 * Edit the default/main.yml (not recommended)

##Run
    
  ```ansible-playbook -l hostname sonar.yml```

##Possible issues

