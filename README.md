# IIEC-RISE-2020-DOCKER-PROJECT
This project works on Docker-compose. It will let you launch WORDPRESS server and uses MYSQL as permanent storage.
## Objective-
* It helps you to access your own wordpress server from anywhere in the world without paying for public IP. 
* Storage of data is permanent.
* Nobody can access your server, without your permission
## Scope-
Helpful when you want only specific people (with whome you share the link) from remote area can access the site and share their views.
## Requirements-
* RedHat8/Centos:latest (As base OS)
* Interent connectivity
* latest version of Docker and Docker-compose
* ngrok software (only if you want to access the site outside LAN network)
## Install Docker in REdHat8 (prerequisite-yum configured)-
* login as root, open terminal
* `cd /etc/yum.repos.d/` 
* `gedit docker.repo` (a repository file will be created. you can use any name.repo) 
* In the docker.repo paste this this url https://download.docker.com/linux/centos/docker-ce.repo and type
* Now, run `yum install docker-ce --nobest`
