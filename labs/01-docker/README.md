# Lab 01 - Building & Running a Docker Image

For this lab, you'll need to be in the `~/environment/eks/labs/01-docker` directory in Cloud9:

```bash
cd ~/environment/eks/labs/01-docker
```

## Build image based at the Dockerfile

```bash
docker build -t python-app .
```

## Run container from the image

```bash
docker run -p 5000:5000 python-app
```

## Is the container running? 

```bash
docker ps
```

## Is the application accessible? 

```bash
curl -I localhost:5000
```

## How to connect to container 

```bash
docker exec -it <container-ID> /bin/bash
```
