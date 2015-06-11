## MySQL-5.1 Docker  ##


## Create MySQL-5.1 Docker Image ##
Clone this repository and execute the following command on your host

```bash
$ git clone https://github.com/bkmukund/docker-mysql-5.1.git
$ cd docker-mysql-5.1/
$ sudo docker build -t mysql .
```

## Run MySQL Container ##
Execute the following command.

```bash
$ sudo docker run --name="mysql"  -d -p 3306:3306 mysql
```

## Now use MySQL 

User: root 
Password: root
