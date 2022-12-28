# Docker-Labs

## lab1

### Problem 1

1. Run the container hello-world

```
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

```
# docker rm containerId
sudo docker rm 5d62

```

5. Remove the image

```

sudo docker image rm hello-world 
```


### Problem 2

1. Run container centos or ubuntu in an interactive mode

```
# -i :run container in interactive mod
sudo docker run -i ubuntu
```

2. Run the following command in the container “echo docker ”

```
# display docker word
echo docker

```


3.Open a bash shell in the container and touch a file named hello-docker

In shell 
```
# create file
touch hello-docker
```

4. Stop the container and remove it. Write your comment about the file hello-docker

```
# docker stop cntainerId 
 sudo docker stop e67de2
```

```
# docker remove containerId
sudo docker rm e67de2
```
when removing container the file removed also


5. Remove all stopped containers

```
#-f : all stoped container
sudo docker rm -f
```

### Problem 3

1. Run a container httpd with name apache and attach a volume to the container 
   a. Volume for containing static html file

```
sudo docker run -it -v apachevol:/usr/local/apache2/htdocs -p 8090:80 --name apache httpd bash
```

2. Remove the container

```
sudo docker rm 9cd83
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
[/home/shrouk/Music/p4.png]

3. Commit the container with image name my apache

```
sudo docker commit 2e89199be9cf  myapache
```

4. Create a dockerfile for ngnix and build the image from this dockerfile
