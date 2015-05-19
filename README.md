## NuoDB Docker for Development ##
[NuoDB](http://www.nuodb.com) is a scale-out SQL database for the cloud and the modern datacenter. It is the NewSQL solution you need to simplify application deployment.

## Requirements ##
You should have the host installed with [Docker](https://docs.docker.com/). For Mac/Windows use [boo2docker](http://boot2docker.io/) as Docker host.

## Determining If Transparent Huge Page (THP) is Enabled ##
Before you install NuoDB, you might want to determine if THP is enabled on your Linux / boot2docker host. 

```bash
$ cat /sys/kernel/mm/transparent_hugepage/enabled
[always] madvise never
```
## Disable THP ##
This should be done on your Linux / boot2docker host as Docker mount these file systems as read-only on docker container

```bash
$ echo never > /sys/kernel/mm/transparent_hugepage/enabled
$ echo never > /sys/kernel/mm/transparent_hugepage/defrag
$ cat /sys/kernel/mm/transparent_hugepage/enabled
always madvise [never]
```

## Create NuoDB Docker Image ##
Clone this repository and execute the following command on your host

```bash
$ git clone git://github.com/mgodekere/nuodb-dev-docker.git
$ cd nuodb-dev-docker
$ docker build -t nuodb2.2 .
```

## Run NuoDB Container ##
Execute the following command.

```bash
$ docker run --name="nuodb2.2c" -d -p 8888:8888 -p 9001:9001 -p 48004:48004 -p 9222:22 nuodb2.2
```
## Access NuoDB Admin Page  ##

```bash
http://<host/boot2docker>:8888/
```
Follow the instructions @ [Nuodb Admin Center](http://doc.nuodb.com/display/doc/Admin+Center) 

## SSH into NuoDB Container  ##

```bash
$ ssh -p 9222 root@localhost
```
Password: root
