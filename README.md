# Flow-2: Create a new Docker Image, Run as Container and Push to Docker Hub

## Pre-requisite Step
- Create your Docker hub account. 
- https://hub.docker.com/
- **Important Note**: In the below listed commands wherever you see **venuch24** you can replace with your docker hub account id. 


## Step-1: Run the base Nginx container
- Access the URL http://localhost
```
docker run --name mynginxdefault -p 80:80 -d nginx
docker ps
docker stop mynginxdefault
```

## Step-2: Create Dockerfile and copy our customized index.html
- **Dockerfile**
```
FROM nginx
COPY index.html /usr/share/nginx/html
```

## Step-3: Build Docker Image & run it
```
docker build -t venuch24/nginx_image:v1 .
docker run --name mynginx1 -p 80:80 -d venuch24/nginx_image:v1

Replace your docker hub account Id
docker build -t <your-docker-hub-id>/nginx_image:v1 .
docker run --name mynginx1 -p 80:80 -d <your-docker-hub-id>/nginx_image:v1
```

## Step-4: Tag & push the Docker image to docker hub
```
docker images
docker tag venuch24/nginx_image:v1 venuch24/nginx_image:v1-release
docker push venuch24/nginx_image:v1-release

Replace your docker hub account Id
docker tag <your-docker-hub-id>/nginx_image:v1 <your-docker-hub-id>/nginx_image:v1-release
docker push <your-docker-hub-id>/nginx_image:v1-release
```
## Step-5: Verify the same on docker hub
- Login to docker hub and verify the image we have pushed
- Url: https://hub.docker.com/repositories