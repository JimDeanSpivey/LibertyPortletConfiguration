# LibertyPortletConfiguration
Configuration to run WebSphere Liberty with portlets.  Also deploys a test portlet to verify that your configuration for running portlets is correct.

## Quick Start
### With Docker
```sh
docker-compose up
```
Navigate to <http://localhost:9080/.SampleLibertyPortlet/SampleLibertyPortlet>

### Without Docker
Place files under usr/servers/{serverName} 

Run the following command to install required features
```sh
bin/installUtility install {serverName}
```

and run bin/server start

Navigate to <http://localhost:9080/.SampleLibertyPortlet/SampleLibertyPortlet>

## Initial setup
### With Docker
1. Install Docker for whatever platform you have.
2. Run command to start server in container
```sh
docker-compose up
```

### Without Docker
#### Requirements
Must have Java 1.7+ JRE installed and have JAVA_HOME set properly.

#### Install WebSphere Liberty
Navigate to <https://developer.ibm.com/wasdev/downloads/liberty-profile-using-non-eclipse-environments/> and download the zip archive.
Extract the archive to any location under your control. To avoid windows filepath length issues make that folder as near root as possible.

#### Create Server
Navigate to the extracted Liberty installation and run the following command to create a server.
```sh
bin/server create {serverName ex 'defaultServer'}
```

#### Install files

Place files under usr/servers/{serverName} 

#### Install features

Run the following command to install features.
```sh
bin/installUtility install {serverName}
```

## Usage
### Start server
```sh
bin/server start
```
View test servlet at

<http://localhost:9080/.SampleLibertyPortlet/SampleLibertyPortlet>

### Install QMAT

#### Install Portlet
Build the UI portlet application and place the resulting WAR file in dropins.

#### Install JMS Service
Build the JMS Service application and place the WAR file in dropins.

### Admin Service
This starts as disabled if you want it make sure you uncomment the admin feature in addition to the security config tag before running docker-compose or install.
<https://localhost:9443/adminCenter> 

username:admin 

password:adminpwd

## References
Document that helped me set this up <https://www.ibm.com/developerworks/community/blogs/7e2e8015-bf72-43b6-bacd-36565b67febc/entry/Using_WebSphere_Application_Server_for_Liberty_profile_to_deploy_and_run_Portlets?lang=en>

## Docker Issues on Windows
Docker on windows is pretty new.  Ensure you have configured it to share your C drive. I was forced to follow these additional instructions to get it to work.<https://forums.docker.com/t/volume-mounts-in-windows-does-not-work/10693/25?u=ksmithorn97>
