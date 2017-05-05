# dockerfiles-centos

# Docker integration with Nuage
In this example of integrating docker with Nuage, after the "VRS" and "docker-monitor" has been deployed and verified, you can run the following command to link a container with a Nuage enterprise/domain/zone and subnet.

Install git:

	# yum -y install git
	
Create a directory that you want to clone the repo to and change directory to it:

	# mkdir -p /root/docker/centos7
	# cd /root/docker/centos7

Clone the repo to your docker host:

	# git clone https://github.com/scottairwin/dockerfile-centos.git

Build the container (note: you can utilize whatever username you want, I'm using "sirwin"):

	# docker build -t sirwin/ssh:centos7 .

To run:

```
# docker run -d -i -t -e "NUAGE-ENTERPRISE=acmecorp" -e "NUAGE-DOMAIN=Docker Domain" -e "NUAGE-ZONE=Docker Zone 1" -e "NUAGE-NETWORK=Subnet 1" -e "NUAGE-USER=docker" --name=centos1 --net=none sirwin/ssh:centos7
```
```
# docker ps
CONTAINER ID        IMAGE               COMMAND               CREATED             STATUS              PORTS               NAMES
39be8c7f5284        sirwin/ssh:centos7    "/usr/sbin/sshd -D"   11 minutes ago      Up 11 minutes                           centos2
```
