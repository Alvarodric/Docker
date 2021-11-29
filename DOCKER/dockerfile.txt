### node.dockerfile ### 
```
FROM node:alpine
LABEL author ="Alvaro Barber'
```

#Specify env variables
```
ENV  NODE_ENV=production
ENV  PORT=3000
```
#Specify Working directory
```
WORKDIR  /var/www
```
#Copy this files from local directory to WORKDIR directory specified(in this case /var/www)
```
COPY  package.json package-lock.json ./ 
```
#Run the commands inside the shell
```
RUN  npm install
```
#First dot is to say copy from current directory to the WORKDIR directory specified(in this case /var/www) and specified by ./
```
COPY . ./
```
#Expose the port (in this case we are taking from env variable PORT)
```
EXPOSE $PORT  
```
#Specifiy what to run when it starts up
```
ENTRYPOINT ["node", "server.js"]
```
--------------------------------------------------------------------------------------------------------------------------------

#In order to build the image
```
docker build -t nodeapp .
docker build -t <registry name>/<image name>:<tag> .
docker build -t alvarobarber/nodeapp:1.0 .
```
#Push to a registry
```
docker push <user name>/<image name>:<tag>
docker push alvarobarber/nodeapp:1.0
docker pull alvaro/nodeapp:1.0
```

--------------------------------------------------------------------------------------------------------------------------------
### .dockerignore ###

# It Works as .gitignore and you can say which files you dont want to copy
