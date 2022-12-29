# Docker-Labs

## lab2

### Problem 1

1. Create your own nginx docker image based on ubuntu “NEVER USE FROM nginx”
    • Install nginx
    • Two index.html one as file and another as .tar "/var/www/html"
    • Expose
    • Start
    • Port mapping

```bash
# write instructions in dockerfile
touch Dockerfile
```

```
sudo docker build -t nginximg:1.0 .
```

```
sudo docker run --name con-nginx -p 8080:80 nginximg
```
- Access templete.html with port 8080



### Problem 2

1 .Create react app docker container "using single stage, Multi-Stage Dockerfile"


https://jsramblings.com/dockerizing-a-react-app/


### Problem 3

1. What is the rest of Docker Networks ? “Name and Definition”

```
    - bridge: The default network driver. Bridge networks are usually used when your applications run in standalone containers 

    - host: For standalone containers, remove network isolation between the container and the Docker host, and use the host’s networking directly.

    - overlay: Overlay networks connect multiple Docker daemons together and enable swarm services to    communicate with each other. 

    - ipvlan: IPvlan networks give users total control over both IPv4 and IPv6 addressing. The VLAN driver builds on top of that in giving operators complete control of layer 2 VLAN tagging and even IPvlan L3 routing for users interested in underlay network integration.

    - macvlan: Macvlan networks allow you to assign a MAC address to a container, making it appear as a physical device on your network. The Docker daemon routes traffic to containers by their MAC addresses. 

    - none: For this container, disable all networking. Usually used in conjunction with a custom network driver. none is not available for swarm services.

```


### Problem 4

1. Create your bridge network, two containers from ubuntu image with different names and try to ping each other using NAME.

```
# docker network create <networkName>
sudo docker network create my-net
```

```bash
# list your docker networks
sudo docker network ls
```

OUTPUT
```bash
NETWORK ID     NAME      DRIVER    SCOPE
4273519e6e58   bridge    bridge    local
247cb8ad0b53   host      host      local
b4b431bf9548   my-net    bridge    local
54368373e0d4   none      null      local

```

```bash
# -dit : run  two containers in background and in interactive mod 
# --network : connect containers to created network
sudo docker run -dit --name ubuntu1 --network my-net ubuntu
sudo docker run -dit --name ubuntu2 --network my-net ubuntu

```

```bash 
sudo docker exec -it ubuntu1 ping ubuntu2
```







