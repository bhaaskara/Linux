# Tomcat installation on EC2 instance
- Follow this video lecture in Valaxy Technologies **[YouTube Channel](https://youtu.be/68WNroQBUts)**  
- Complete DevOps Project course on [Udemy](https://www.udemy.com/course/valaxy-devops/?referralCode=8147A5CF4C8C7D9E253F)  
### Pre-requisites
1. EC2 instance with Java 11
### Install Apache Tomcat
1. Download tomcat packages from  https://tomcat.apache.org/download-80.cgi onto /opt on EC2 instance
   > Note: Make sure you change `<version>` with the tomcat version which you download. 
   ```sh 
   # Create tomcat directory
   cd /opt
   wget http://mirrors.fibergrid.in/apache/tomcat/tomcat-8/v8.5.35/bin/apache-tomcat-8.5.35.tar.gz
   tar -xvzf /opt/apache-tomcat-<version>.tar.gz
   ```
1. give executing permissions to startup.sh and shutdown.sh which are under bin. 
   ```sh
   chmod +x /opt/apache-tomcat-<version>/bin/startup.sh 
   chmod +x /opt/apache-tomcat-<version>/bin/shutdown.sh
   ```
   > Note: you may get below error while starting tomcat incase if you dont install Java   
   `Neither the JAVA_HOME nor the JRE_HOME environment variable is defined At least one of these environment variable is needed to run this program`
1. create link files for tomcat startup.sh and shutdown.sh 
   ```sh
   ln -s /opt/apache-tomcat-<version>/bin/startup.sh /usr/local/bin/tomcatup
   ln -s /opt/apache-tomcat-<version>/bin/shutdown.sh /usr/local/bin/tomcatdown
   tomcatup
   ```
  #### Check point :
access tomcat application from browser on port 8080  
 - http://<Public_IP>:8080

  Using unique ports for each application is a best practice in an environment. But tomcat and Jenkins runs on ports number 8080. Hence lets change tomcat port number to 8090. Change port number in conf/server.xml file under tomcat home
   ```sh
 cd /opt/apache-tomcat-<version>/conf
# update port number in the "connecter port" field in server.xml
# restart tomcat after configuration update
tomcatdown
tomcatup
```
#### Check point :
Access tomcat application from browser on port 8090  
 - http://<Public_IP>:8090

1. now application is accessible on port 8090. but tomcat application doesnt allow to login from browser. changing a default parameter in context.xml does address this issue
   ```sh
   #search for context.xml
   find / -name context.xml
   ```
1. above command gives 3 context.xml files. comment (<!-- & -->) `Value ClassName` field on files which are under webapp directory. 
After that restart tomcat services to effect these changes. 
At the time of writing this lecture below 2 files are updated. 
   ```sh 
   /opt/tomcat/webapps/host-manager/META-INF/context.xml
   /opt/tomcat/webapps/manager/META-INF/context.xml
   
   # Restart tomcat services
   tomcatdown  
   tomcatup
   ```
1. Update users information in the tomcat-users.xml file
goto tomcat home directory and Add below users to conf/tomcat-users.xml file
   ```sh
	<role rolename="manager-gui"/>
	<role rolename="manager-script"/>
	<role rolename="manager-jmx"/>
	<role rolename="manager-status"/>
	<user username="admin" password="admin" roles="manager-gui, manager-script, manager-jmx, manager-status"/>
	<user username="deployer" password="deployer" roles="manager-script"/>
	<user username="tomcat" password="s3cret" roles="manager-gui"/>
   ```
1. Restart serivce and try to login to tomcat application from the browser. This time it should be Successful

# Install Tomcat on Ubuntu 20.04 - VM
```
1. Install Java runtime environment
2. Install tomcat
```

**1. Install Java run time environment**
```sh
sudo apt update
sudo apt install default-jdk -y
Java --version # Verify java version
```

**2. Install tomcat**
Download the latest version of Apache Tomcat.  
To find the latest Tomcat version, visit the [official download](https://tomcat.apache.org/whichversion.html) page.
```
wget https://archive.apache.org/dist/tomcat/tomcat-10/v10.0.8/bin/apache-tomcat-10.0.8.tar.gz
```

Extract the downloaded archive.
```
sudo tar xzvf apache-tomcat-10.0.8.tar.gz
```

Create an installation directory `/opt/tomcat/`
```
sudo mkdir /opt/tomcat/
```

Move the extracted files to the installation directory.
```
sudo mv apache-tomcat-10.0.8/* /opt/tomcat/
```

Change ownership of the installation directory.
```
$ sudo chown -R www-data:www-data /opt/tomcat/
```

Change access permissions for the installation directory.
```
sudo chmod -R 755 /opt/tomcat/
```

Edit `conf/tomcat-users.xml` file to configure an administrator and manager account for Apache Tomcat.
```
sudo nano /opt/tomcat/conf/tomcat-users.xml
```

Add the code below within the `<tomcat-users>` tag. Change the password for administrator and manager access by changing the value `StrongPassword` below with a high secure password.

```
<!-- user manager can access only manager section -->
<role rolename="manager-gui" />
<user username="manager" password="StrongPassword" roles="manager-gui" />

<!-- user admin can access manager and admin section both -->
<role rolename="admin-gui" />
<user username="admin" password="StrongPassword" roles="manager-gui,admin-gui" />
```

Enable remote access to Apache Tomcat by editing manager and host-manager configuration files. Edit manager application `context.xml` file:

```
$ sudo nano /opt/tomcat/webapps/manager/META-INF/context.xml
```

Comment out the IP addresses section as shown below. Then, save and close the file.

```
<!-- <Valve className="org.apache.catalina.valves.RemoteAddrValve"
         allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" /> -->
```

Edit host manager application `context.xml` file:

```
$ sudo nano /opt/tomcat/webapps/host-manager/META-INF/context.xml
```

Comment out the IP addresses section as shown below. Then, save and close the file.

```
<!--<Valve className="org.apache.catalina.valves.RemoteAddrValve"
         allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" /> -->
```

Create a systemd unit file for Apache Tomcat.

```
$ sudo nano /etc/systemd/system/tomcat.service
```

Add the code below to the file. Then, save and close the file.

```
[Unit]
Description=Tomcat
After=network.target

[Service]
Type=forking

User=root
Group=root

Environment="JAVA_HOME=/usr/lib/jvm/java-1.11.0-openjdk-amd64"
Environment="JAVA_OPTS=-Djava.security.egd=file:///dev/urandom"
Environment="CATALINA_BASE=/opt/tomcat"
Environment="CATALINA_HOME=/opt/tomcat"
Environment="CATALINA_PID=/opt/tomcat/temp/tomcat.pid"
Environment="CATALINA_OPTS=-Xms512M -Xmx1024M -server -XX:+UseParallelGC"

ExecStart=/opt/tomcat/bin/startup.sh
ExecStop=/opt/tomcat/bin/shutdown.sh

[Install]
WantedBy=multi-user.target
```

Reload the systemd daemon service to apply changes.

```
$ sudo systemctl daemon-reload
```

Start Apache Tomcat service.

```
$ sudo systemctl start tomcat
```

Enable the service to start up on system boot.

```
$ sudo systemctl enable tomcat
```

Check the status of the service.

```
$ sudo systemctl status tomcat
```

Access tomcat webUI on `http://serverIPaddress:8080`

# Install Tomcat on Centos 7 - VM
`sudo apt install tomcat -y`
This will install Tomcat and its dependencies, including Java.
