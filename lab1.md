# Docker-Labs

## lab1

### Problem 1

1. Run the container hello-world

```bash
# docker run imageName 
sudo docker run hello-world

```

2. Check the container status

``` 
sudo docker ps -a
```

3. Start the stopped container

```
sudo docker start 5d62

```

4. Remove the container

```bash
# docker rm containerId
sudo docker rm 5d62

```

5. Remove the image

```

sudo docker image rm hello-world 
```


### Problem 2

1. Run container centos or ubuntu in an interactive mode

```bash
# -i :run container in interactive mod
sudo docker run -i ubuntu
```

2. Run the following command in the container “echo docker ”

```bash
# display docker word
echo docker

```


3.Open a bash shell in the container and touch a file named hello-docker

In shell 
```bash
# create file
touch hello-docker
```

4. Stop the container and remove it. Write your comment about the file hello-docker

```bash
# docker stop cntainerId 
 sudo docker stop e67de2
```

```bash
# docker remove containerId
sudo docker rm e67de2
```
when removing container the file removed also


5. Remove all stopped containers

```bash
#-f : all stoped container
#sudo docker rm -f
sudo docker container prune 
```

### Problem 3

1. Run a container httpd with name apache and attach a volume to the container 
   a. Volume for containing static html file

```
sudo docker run -it -v apachevol:/usr/local/apache2/htdocs -p 8090:80 --name apache httpd bash
```
In shell
```
touch /usr/local/apache2/htdocs/page.html
```

```
echo "Hello From Page.html" >> /usr/local/apache2/htdocs/page.html 
```


2. Remove the container

```
sudo docker rm 5e2096c15141
```

3. Run a new container with the following:
    • Attach the volume that was attached to the previous container
    • Map port 80 to port 9898 on you host machine
    • Access the html files from your browser

```
sudo docker run -it -v apachevol:/usr/local/apache2/htdocs/ -p 9898:80 --name apachenew httpd bash

```

### Problem 4

1. Run the image httpd again without attaching any volumes 

```
sudo docker run -it  -p 9898:80 --name problem4 httpd bash
```

2. Add html static files to the container and make sure they are accessible
   
In shell
```
touch new.html
```
```
echo "Welcom to new html file" >> new.html
```
![p4](https://user-images.githubusercontent.com/57557314/209865181-1a34a33e-4b6a-459e-beed-dcf51aa8a3d6.png)


3. Commit the container with image name my apache

```
sudo docker commit 2e89199be9cf  myapache
```

4. Create a dockerfile for ngnix and build the image from this dockerfile

```bash
#Dockerfile without extention
touch Dockerfile
```
```bash
# . means current dir , OR path of Dockerfiles
# -t <tagName>
sudo docker build . -t mynginx
```
```
sudo docker images
```
OUTPUT
```
REPOSITORY   TAG       IMAGE ID       CREATED          SIZE
mynginx      latest    1c6952d7fdc8   39 seconds ago   142MB
```

### Problem 5

1. Create a volume called mysql_data, then deploy a MySQL database called app-database. Use the mysql latest image, and use the -e flag to set MYSQL_ROOT_PASSWORD to P4sSw0rd0!.Mount the mysql_data volume to /var/lib/mysql.The container should run in the background.

```
sudo docker volume create mysql_data
```

```bash
# list all volumes in docker engine
sudo ls /var/lib/docker/volumes

#OUTPUT

apachevol  backingFsBlockDev  metadata.db  mysql_data

```



```bash
#-d : run container in background
sudo docker run -d --name app-database --mount type=volume,source=mysql_data,target=/var/lib/mysql -e MYSQL_ROOT_PASSWORD=P4ssW0rd0! mysql:latest
```
