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