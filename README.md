# IIEC-RISE-1.0-DOCKER-PROJECT
This project works on Docker-compose. 
# Table of Contents
- Objective
- Scope
- Working
- Requirements
- Install Docker in REdHat8
- Create Volumes
- Install Docker-compose
- Create Infrastucture of code
- To Launch the server
- To access
- Problems you may face
- To stop 
- Bibliography
# Objective
- It helps you to access your own wordpress server from anywhere in the world without paying for public IP. 
- Storage of data is permanent.
- Nobody can access your server, without your permission 
# Scope
- Helpful when you want only specific people (with whome you share the link) from remote area can access the site and share their views.
- Site will be accessible untill the servers are up
# Working
After you do the installation (as mentioned below) 
* Automatically mysql and wordpress, docker images will be pulled from internet
* Wordpress will get connected to mysql (as database)
* Both will get attached to their respective permanent storage (volumes)
* Traffic of base OS will get trasfered to docker containers through PATting
# Requirements
* RedHat8/Centos:latest (As base OS)
* Internet connectivity
* latest version of Docker and Docker-compose
* ngrok software (only if you want to access the site outside LAN network) 
(software is provided)
# Install Docker in REdHat8 
Prerequisite-yum configured-
* login as root, open terminal
* Run command- `cd /etc/yum.repos.d/`
![go to yum](https://github.com/jarvistyro/IIEC-RISE-2020-DOCKER-PROJECT/blob/master/go%20to%20yum%20repositories.png)

* Now, (To create a repository file, you can use any name.repo)   
`gedit docker.repo` 
![make docker repo](https://github.com/jarvistyro/IIEC-RISE-2020-DOCKER-PROJECT/blob/master/create%20docker%20repository.png)
* In the docker.repo paste this this url (https://download.docker.com/linux/centos/7/x86_64/stable/) and type
![content of docker repo](https://github.com/jarvistyro/IIEC-RISE-2020-DOCKER-PROJECT/blob/master/content%20of%20docker%20repository.png)
* Run
`yum install docker-ce --nobest` 
![install docker](https://github.com/jarvistyro/IIEC-RISE-2020-DOCKER-PROJECT/blob/master/cmd%20to%20install%20docker.png)
* ## To verify 
`docker version` 
![verify](https://github.com/jarvistyro/IIEC-RISE-2020-DOCKER-PROJECT/blob/master/verify%20docker%20version.png)
* ## Start Docker
```
systemctl start docker
`systemctl enable docker
```
![demo](https://github.com/jarvistyro/IIEC-RISE-2020-DOCKER-PROJECT/blob/master/start%20n%20enable%20docker.png)
# Create Volumes 
```
docker volume create sql_store
docker volume create wp_store
``` 
![demo](https://github.com/jarvistyro/IIEC-RISE-2020-DOCKER-PROJECT/blob/master/create%20volume.png)
kindly keep the same names to avoid any manual changes (if you want you can change)
# Install Docker-compose
* ## To download software run
`curl -L https://github.com/docker/compose/releases/download/1.21.2/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose`
![demo](https://github.com/jarvistyro/IIEC-RISE-2020-DOCKER-PROJECT/blob/master/install%20docker%20compose.png)
* ## Now, to make the software executable
`chmod +x /usr/local/bin/docker-compose`
![demo](https://github.com/jarvistyro/IIEC-RISE-2020-DOCKER-PROJECT/blob/master/make%20docker%20compose%20executable.png)
* ## To verify if it's installed
`docker-compose version`
![demo](https://github.com/jarvistyro/IIEC-RISE-2020-DOCKER-PROJECT/blob/master/to%20verify%20compose%20version.png)
# Create Infrastucture of code
* To create a folder/directory (choose name accordingly) 
`mkdir /mycompose`
* Create a "docker-compose.yml" (mandatory in our case to use same name)
```
cd /mycompose
ls
vim docker-compose.yml
```
![demo](https://github.com/jarvistyro/IIEC-RISE-2020-DOCKER-PROJECT/blob/master/open%20compose.yml.png)
* copy file (https://github.com/jarvistyro/IIEC-RISE-2020-DOCKER-PROJECT/blob/master/docker-compose) in docker-compose.yml
1[demo](https://github.com/jarvistyro/IIEC-RISE-2020-DOCKER-PROJECT/blob/master/yml%20file.png)
# To Launch the server 
```
cd /mycompose
ls
docker-compose up
```
![demo](https://github.com/jarvistyro/IIEC-RISE-2020-DOCKER-PROJECT/blob/master/docker%20compose%20up.png)
# To access
* ## Locally (LAN)
* Find your base OS's IP using `ifconfig`
* Go to any other device in your local network
* Open web browser, search in url "BaseOS_IP:8080"
* ## Globally 
* Copy in Desktop folder of base OS(RedHat)
* Unzip using 
```
cd /Desktop
unzip ngrok.zip
ls
./ngrok http 8080
```
* A URL will be genetared, share it..
![demo](https://github.com/jarvistyro/IIEC-RISE-2020-DOCKER-PROJECT/blob/master/Ngrok.jpg)
* ## Now the world can connet...
* ## We are all set... Go ahead start writing your blog
* ## Share the URL and let others join.
![demo](https://github.com/jarvistyro/IIEC-RISE-2020-DOCKER-PROJECT/blob/master/Access%20loacally.png)
![demo](https://github.com/jarvistyro/IIEC-RISE-2020-DOCKER-PROJECT/blob/master/first%20blog.png)
# Problems you may face
Linux's firewall will not allow external traffic to enter. So, disable it and change iptables policy to FORWARD and ACCEPT
```
1. systemctl stop firewalld
2. setenforce 0
3. iptables -F
4. iptables -P FORWARD ACCEPT
5. systemctl restart docker 
```
# To stop
* ngrok : ctrl+c                           // now only LAN devices can access
* docker compose :  `docker-compose stop`  //We are shuting our servers down- site will not be accessible any more
# Bibliography
* IIEC RISE 1.0 DOCKER (https://www.youtube.com/watch?v=3Kn6_b-1mK4&list=PLAi9X1uG6jZ30QGz7FZ55A27jPeY8EwkE) 
* IIEC CONNECT 1.0 (https://www.youtube.com/channel/UCtY-JhEZ3iPLtozWGgd2efQ)
* Google (https://www.google.com/)
* RedHat 8 (https://developers.redhat.com/rhel8/)
* Docker (https://docs.docker.com/docker-hub/official_images/)
* ngrok (https://ngrok.com/)



