1. Create the Angular app

```
ng new my-docker-angular-app
```

2. Create a Dockerfile in the main folder
3. Create a .dockerignore file in the main folder. This file works similar to a .gitignore file and ignores files that are specified while creating the docker image.
4. Create a nginx.conf file in the main folder.

Setting the "listen" directive to 80 or whatever port is exposed in the Dockerfile.

5. Create a docker image.

```
docker build -t ng-docker-app:v1.0.0 -f ./Dockerfile .
```

* -t: Tag ("Latest" by default)
* -f: File (Path to Dockerfile)

Checking the list of docker images in your system:

```
docker image ls
```

6. Create a docker container

```
docker run -p 8000:80 -d ng-docker-app:v1.0.0
```

* -p: Port

Define a port on which the container will be hosted and also the port on which the app is hosted inside the container.

Syntax: \<host-port>:\<docker-port>

* -d: Detach

If not specified, the docker will keep the console running.

If you exposed port 80 in the Dockerfile and assigned NGINX to listen to port 80, \<docker-port> must be the 80 as well.

Getting the list of currently running containers in your system:
```
docker container ls
```

7. Now, the container should be running. You can try viewing it on localhost:8000.