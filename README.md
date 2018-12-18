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
### Docker Build and Run
+ `docker build -t username/name:tag .` build docker file
+ `docker run <image-name>` run docker file
+ `docker run -p <o/p port>:<i/p port>  username/name:tag` run docker file exposed at input port

--------------------------

### PUSH docker file 
+ `docker push username/name` push dockerfile to docker hub
+ `docker push username/name:tag` push dockerfile with new tag




### Docker Images
+ `docker images` list docker images
+ `docker image ls` list docker images 
+ `docker image rm <image ID>` remove a docker image
+ `docker image rm $(docker image ls -aq)` remove all images

------------------------
### Docker Containers
+ `docker container ls` list running containers
+ `docker container ls --all` list all in running and quiet mode
+ `docker container ls -aq` list all container IDs
+ `docker container stop <container ID>` stop a docker container
+ `docker container stop $(docker container ls -aq)` stop all containers
+ `docker container rm <container ID>` remove a docker container
+ `docker container rm $(docker container ls -aq)` remove all containers
----------------------------------------
## Dockerfile
1. Assuming the project structure is standard and will build the app like 
a generic Go app.
    
    ```dockerfile
       FROM golang:onbuild
    ```
    
2. Customize Dockerfile example 1
    ```dockerfile
    FROM golang:latest
    RUN mkdir /app
    ADD . /app/
    WORKDIR /app
    RUN go build 
    CMD ["/app/app"]
    ```
3. Customize Dockerfile example 2
    ```dockerfile
    FROM golang:latest
    RUN go get -u github.com/spf13/cobra/cobra
    COPY . /go/src/temp
    WORKDIR /go/src/temp
    RUN go build
    CMD ["start"]
    ENTRYPOINT ["/go/src/temp/temp"]
    ```
4. Docker file example using Binary file 
    ```dockerfile
    FROM busybox:glibc
    
    COPY BookListApi /bin/api
    
    ENTRYPOINT ["/bin/api"]
    
    EXPOSE 8000
    ```
5. Docker file example having port output 
    ```dockerfile
    FROM golang:latest
    RUN go get -u github.com/spf13/cobra/cobra
    RUN go get -u github.com/gorilla/mux
    COPY . /go/src/github.com/kamolhasan/BookListApi
    WORKDIR /go/src/github.com/kamolhasan/BookListApi
    RUN go build
    ENTRYPOINT ["/go/src/github.com/kamolhasan/BookListApi/BookListApi"]
    EXPOSE 8000
    ```
 