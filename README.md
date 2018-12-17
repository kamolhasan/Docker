# Docker CheetSheet

### Remove `sudo` from  `docker` command 

1. Create the `docker` group
    ```
    sudo groupadd docker
    ```
   
2. Add your user to the `docker` group
    ```
    sudo usermod -aG docker $USER
    ```
3. Log out and log back in so that your group membership is re-evaluated

----------------------------
### Version

+ `docker --version` test docker version
+ `docker info` to view in details about docker installation

---------------------------

### Execute Docker Image
+ `docker run <image-name>` 

--------------------------

### List Docker Images
+ `docker images`
+ `docker image ls`
------------------------
### List Docker Containers
+ `docker container ls` list running containers
+ `docker container ls --all` list all in running and quiet mode
