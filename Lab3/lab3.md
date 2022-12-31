# Docker-Labs

## Lab3

### Problem 1

1. Convert the created react app multi-stage docker image into compose format


```
touch docker-compose.yml
```

```
sudo docker-compose up -d
```
```bash
docker-compose ps
```
OUTPUT
```
 Name                   Command               State                  Ports                
---------------------------------------------------------------------------------------------
con-react-app   /docker-entrypoint.sh ngin ...   Up      0.0.0.0:3000->80/tcp,:::3000->80/tcp

```

- Access con-react-app with port 3000
 
![3-p1](https://user-images.githubusercontent.com/57557314/210154991-ffb80227-0f41-48a9-8265-7aeb8715cada.png)



### Problem 2

1. Create flask app to count number of visits to browser:
     - Create new directory called flask then add app.py and requirements.txt files
     - Create Dockerfile for the python app
     - Create docker-compose for the app and use Redis as temp DB.

```
touch Dockerfile
```

```
touch docker-compose.yml
```

```
sudo docker-compose up -d
```
```
sudo docker-compose ps
```
OUTPUT

```
 Name                 Command               State    Ports
------------------------------------------------------------
python-con   python app.py                    Exit 0        
redis-con    docker-entrypoint.sh redis ...   Exit 0    
```
- Access python app

![l3-p2](https://user-images.githubusercontent.com/57557314/210155020-b6a03aa4-57db-4fff-b2da-cce2a7e92580.png)


