kill all running containers with
```
docker kill $(docker ps -q)
```

delete all stopped containers with docker
```
rm $(docker ps -a -q)
```

delete all images with
```
docker rmi $(docker images -q)
```

update and stop a container that is in a crash-loop with
```
docker update –restart=no && docker stop
```

If you want to clean up and delete all unused container images, just add -a
```
docker image prune -a
```
