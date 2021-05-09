## Cleanup 
Stop and delete all running containers
```shell
docker ps
docker stop [CONTAINER-ID]
docker rm [CONTAINER-ID] [CONTAINER-ID] [CONTAINER-ID] 
```
Delete the images that you have created earlier
```shell
docker image ls
docker rmi [IMAGE-ID] [IMAGE-ID] [IMAGE-ID]
```
