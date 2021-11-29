### node.dockerfile ### 
```
FROM node:alpine
LABEL author ="Alvaro Barber'
```

Specify env variables
```
ENV  NODE_ENV=production
ENV  PORT=3000
```
Specify Working directory
```
WORKDIR  /var/www
```
Copy this files from local directory to WORKDIR directory specified(in this case /var/www)
```
COPY  package.json package-lock.json ./ 
```
Run the commands inside the shell
```
RUN  npm install
```
First dot is to say copy from current directory to the WORKDIR directory specified(in this case /var/www) and specified by ./
```
COPY . ./
```
Expose the port (in this case we are taking from env variable PORT)
```
EXPOSE $PORT  
```
Specifiy what to run when it starts up
```
ENTRYPOINT ["node", "server.js"]
```
--------------------------------------------------------------------------------------------------------------------------------
### Docker Build ###

In order to build the image
```
docker build -t nodeapp .
docker build -t <registry name>/<image name>:<tag> .
docker build -t alvarobarber/nodeapp:1.0 .
```
Push to a registry
```
docker push <user name>/<image name>:<tag>
docker push alvarobarber/nodeapp:1.0
docker pull alvaro/nodeapp:1.0
```

--------------------------------------------------------------------------------------------------------------------------------
### .dockerignore ###

It Works as .gitignore and you can say which files you dont want to copy

-------------------------------------------------------------------------------------------------------------------------------
### Docker Run ### 

docker run -p <externalPort>:<internalPort> -d <imageName> (-d is used for not locking the console "detached") 
```
docker run -p 8080:80 -d nginx:alpine
docker ps -a 
docker stop ce
docker remove ce
```
### Docker Logs ###   
```
docker logs
```
  
### Docker Container Volumes ###
  
Volume is located in /var/www/logs but we can create a volume mount so if container dies , data is not lost
```
docker run - p <ports> -v /var/www/logs <imageToRun>
```
### Shell into a container ###
  
```
docker exec -it <containerId> sh  
```
