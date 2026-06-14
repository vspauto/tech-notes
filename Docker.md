# Docker tech note

## Install

Install Docker Desktop on Windows. [Docker Install](https://docs.docker.com/desktop/setup/install/windows-install/)  
It provides small Linux Destribution.<br>



## commands

**Download Docker image** from [GockerHub repository](https://hub.docker.com/)
```bash
docker pull image_name:tag
ex: docker pull ngnix:1.31
```

**Docker image list**
```bash
docker images
ex: 
IMAGE                             ID             DISK USAGE   CONTENT SIZE   EXTRA
docker/welcome-to-docker:latest   c4d56c24da4f       22.2MB         6.03MB   U
nginx:1.31                        608a100c7165        241MB           66MB
```
**Remove Docker Image**
```bash
docker rmi [image id]
```

**Execute Docker Image**
```bash
docker run image_name:tag
ex: docker run -d -p 8080:80 --name my-nginx nginx:1.31
```
> option
>*   -d: detatch. Run container in background.
>*  --name: assign container name
>*  --rm : Automatically remove the container and its associated anonymous volumes when it exits
>*  -p host_port:container_port : assign host:container port mapping
>*  -it: Connect Termianl Input/Output
>*  -e: set environment
>*  -v: link volume. [host_path:container_path]
>*  -w: assign WORKDIR

Open Broser and type "localhost:8080"
![Welcome Nginx](./pic/docker/WelcomeNginx.png)

**Docker status**
```bash
docker ps
```
>*  -a : all

**Docket stop/run**
```bash
docker stop [contailer_id or container_name]
docker start [contailer_id or container_name]
docker rm [contailer_id or container_name]
```


**Docker logs**
```bash
docker logs container_id
ex: 
$ docker ps
CONTAINER ID   IMAGE                 COMMAND  CREATED    STATUS PORTS  NAMES
ef3d41f56bb2   docker/welcome:latest "..."  ..  0.0.0.0:8088->80/tcp, ...   welcome
$ docker logs ef3d41f56bb2
```


## Prepare Image

**Dockerfile**

| command | Description |
|---------|-------------|
| # | comment |
| FROM | base image |
| WORKDIR | assign working directory |
| COPY | copy command |
| RUN | run command |
| EXPOSE | expose port number |
| CMD ["cmd", "option"] | execution command |

**example**
> FROM python:3.8
>
> WORKDIR /usr/src/app
> 
> COPY . .
>
> RUN pip install --no-cache-dir -r requirements.txt
>
> EXPOSE 5000
>
> CMD ["python", "./app.py"]

**example1**

Prepare app.py
```python
from flash import Flask
app = Flask(__name__)
@app.route('/')
def home():
    return "Hello, Docker!"
    if __name__ == '__main__'
        app.run(host='0.0.0.0', port=5000)
```
Prepare Dockerfile
```Docker
FROM python:3.9-slim

WORKDIR /app/
COPY requirements.txt requirements.txt
COPY app.py app.py
RUN pip install --no-cache-dir -r requirements.txt
CMD ["python", "app.py"]
```

Build Image
```bash
docker build -t flask-app .
```
>* -t flask-app: Name of Image
>* .: current directory

Run container
```bash
docker run -d -p 5000:5000 --name flask-container flash-app
```

Comfirm<br>
Open broswer with http://localhost:5000
Confirm "Hello, Docker!

**example2**

Directory
>src<br>
+- server.js<br>
Dockerfile<br>
package.json<br>

server.js
```java
const express = require('express');
const app = express();

app.get('/', (req,res) => {
    res.send("welcome to my awesome app!");
});
app.listen(3000, function() {
    console.log("app listening on port 3000");
});
```
package.json
```json
{
    "name": "my-app",
    "version": "1.0",
    "dependencies": {
        "express": "4.18.2"
    }
}
```
Dockerfile
```dockerfile
FROM node:19-alpine
COPY package.json /app/
COPY src /app/
WORKDIR /app
RUN npm install
CMD ["node", "server.js"]
```

**Command**
```bash
docker build -t node-app:1.0 .
docker images
IMAGE                             ID             DISK USAGE   CONTENT SIZE   EXTRA
node-app:1.0                      12082cf46d43        262MB         56.2MB
docker run -d -p 3000:3000 --name my-node-app node-app:1.0
docker ps
docker logs my-node-app
```
Open Broser and type "localhost:3000"<br>
![Welcome to my awesome app](./pic/docker/my-node-app.png)


## Docker Compose
**docker-compose.yaml**

```docker
version: "3.8"
services:
  <Service Name>
    image: <Image>
    container_name: <container_name>
    ports:
      - "Host_Port:Container_Port"
    volumes:
      - "Volunm_name/bind_mount:Container_path"
    environment:
      - KEY=VALUE
    depends_on:
      - <Other Service>

networks:
  <network name>
    driver: bridge

volumes:
  <volume name>
    driver: local
```
example:

execute
```bash
docker compose up -d
docker compose down
docker compose logs -f
```

