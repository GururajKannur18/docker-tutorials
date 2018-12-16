# docker useful commands

```
$ docker-machine ip
192.168.99.100
```

```
$ docker --version
Docker version 18.03.0-ce, build 0520e24302
```

```
$ docker-compose --version
docker-compose version 1.20.1, build 5d8c71b2
```

docker pull command will search for alpine into docker hub and pull it.

```
$ docker pull alpine
Using default tag: latest
latest: Pulling from library/alpine
4fe2ade4980c: Pull complete
Digest: sha256:621c2f39f8133acb8e64023a94dbdf0d5ca81896102b9e57c0dc184cadaf5528
Status: Downloaded newer image for alpine:latest
```
NOTE: Images will get pulled from docker hub in layers. 

# Hello-World

```
$ docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
d1725b59e92d: Pull complete
Digest: sha256:0add3ace90ecb4adbf7777e9aacf18357296e799f81cabc9fde470971e499788
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```


Download/fetch the Java8

```
$ docker pull java:8
8: Pulling from library/java
Digest: sha256:c1ff613e8ba25833d2e1940da0940c3824f03f802c449f3d1815a66b7f8c0e9d
Status: Image is up to date for java:8
```

If I want to pull specific/particular image

```
$ docker pull ubuntu:14.04
14.04: Pulling from library/ubuntu
aa1a66b8583a: Pull complete
aaccc2e362b2: Pull complete
a53116a2808f: Pull complete
b3a7298e318c: Pull complete
Digest: sha256:f961d3d101e66017fc6f0a63ecc0ff15d3e7b53b6a0ac500cd1619ded4771bd6
Status: Downloaded newer image for ubuntu:14.04
```

# List Docker Images
```
$ docker images
REPOSITORY                             TAG                 IMAGE ID            CREATED             SIZE
kbastani/movies-ui                     latest              0a107de3a95e        40 minutes ago      761MB
kbastani/movie-microservice            latest              31ca109da9fa        41 minutes ago      819MB
kbastani/consul-microservice           latest              9e0b6f419feb        41 minutes ago      723MB
kbastani/hystrix-dashboard             latest              cb65337bc385        42 minutes ago      696MB
kbastani/config-microservice           latest              e706a42dfb09        43 minutes ago      724MB
kbastani/recommendation-microservice   latest              51cede9d96de        43 minutes ago      819MB
kbastani/api-gateway-microservice      latest              1056ed563cba        44 minutes ago      716MB
kbastani/discovery-microservice        latest              bc7809bb1600        44 minutes ago      726MB
kbastani/users-microservice            latest              ac3f5e3dc295        45 minutes ago      820MB
```

# Remove specific Image, here IMAGE ID = f17b6a61de28

```
$ docker rmi f17b6a61de28
Untagged: ubuntu:14.04
Untagged: ubuntu@sha256:f961d3d101e66017fc6f0a63ecc0ff15d3e7b53b6a0ac500cd1619ded4771bd6
Deleted: sha256:f17b6a61de28594fb3ec53b1cca7164fba66357d1635b414eeed4d586744342e
Deleted: sha256:62faa9fad606573b982c0444778746244947829aa8ebefbf29b3a5291875dc84
Deleted: sha256:5848a5ca21d07333dbdf428bbdde15d5c7cecc7614b24562b49b205d8d20199a
Deleted: sha256:cd509aa64a17350b03bf6af7f41d849fc273a0f2c9d1a309e897380617fca46e
Deleted: sha256:960c7c5516b277c5c23644b2cfb53d0106543eace96d517141611fa34e1b957c
```

# Remove Docker Images

- docker rmi <IMAGE ID>
- docker rmi <IMAGE ID1> <IMAGE ID2>
- docker rmi $(docker images -f "dangling=true" -q)

-quite, -q ==> Only shows numeric Ids
-filter, -f ==> filter output based on condition provided. 

-a, -all => Shows all containers (default shows just running).
-q => Only displays numeric Ids.

- docker images prune
- Removes dangling images (images which are not used by any containers)

# List running containers
```
$ docker ps -a
CONTAINER ID        IMAGE                                  COMMAND                  CREATED             STATUS                        PORTS               NAMES
e91cd8fbe0da        kbastani/hystrix-dashboard             "java -Djava.securit…"   About an hour ago   Exited (137) 31 minutes ago                       docker_hystrix_1
7368e0d8fc42        kbastani/api-gateway-microservice      "java -Djava.securit…"   About an hour ago   Exited (143) 31 minutes ago                       docker_gateway_1
f3cf5171ef33        kbastani/movies-ui                     "java -Djava.securit…"   About an hour ago   Exited (143) 31 minutes ago                       docker_moviesui_1
10ad4716e9b7        kbastani/movie-microservice            "java -Djava.securit…"   About an hour ago   Exited (1) 39 minutes ago                         docker_movie_1
f78f4df9206f        kbastani/users-microservice            "java -Djava.securit…"   About an hour ago   Exited (1) 39 minutes ago                         docker_user_1
fac92c7a4c26        kbastani/recommendation-microservice   "java -Djava.securit…"   About an hour ago   Exited (1) 39 minutes ago                         docker_recommendation_1
e8d4af14ceb6        kbastani/config-microservice           "java -Djava.securit…"   About an hour ago   Exited (143) 31 minutes ago                       docker_configserver_1
6a5223a4b1d1        kbastani/discovery-microservice        "java -Djava.securit…"   About an hour ago   Exited (143) 31 minutes ago                       docker_discovery_1
```

# Kill all running containers

```
docker kill $(docker ps -q)
```

# delete all stop containers
```
docker rmi $(docker ps -a -q)
```

# delete all images
(Note: This will delete all layers of images)
```
docker rmi $(docker images -q)
```









```
$ docker info
Containers: 8
 Running: 0
 Paused: 0
 Stopped: 8
Images: 69
Server Version: 18.06.1-ce
Storage Driver: aufs
 Root Dir: /mnt/sda1/var/lib/docker/aufs
 Backing Filesystem: extfs
 Dirs: 64
 Dirperm1 Supported: true
Logging Driver: json-file
Cgroup Driver: cgroupfs
Plugins:
 Volume: local
 Network: bridge host macvlan null overlay
 Log: awslogs fluentd gcplogs gelf journald json-file logentries splunk syslog
Swarm: inactive
Runtimes: runc
Default Runtime: runc
Init Binary: docker-init
containerd version: 468a545b9edcd5932818eb9de8e72413e616e86e
runc version: 69663f0bd4b60df09991c08812a60108003fa340
init version: fec3683
Security Options:
 seccomp
  Profile: default
Kernel Version: 4.9.93-boot2docker
Operating System: Boot2Docker 18.06.1-ce (TCL 8.2.1); HEAD : c7e5c3e - Wed Aug 22 16:27:42 UTC 2018
OSType: linux
Architecture: x86_64
CPUs: 1
Total Memory: 995.6MiB
Name: default
ID: JCFC:EWS2:IQH7:T7FE:RKJ6:222L:4CZR:KOJZ:TDXN:EXBV:RDI5:QXMN
Docker Root Dir: /mnt/sda1/var/lib/docker
Debug Mode (client): false
Debug Mode (server): false
No Proxy: 192.168.99.100
Registry: https://index.docker.io/v1/
Labels:
 provider=virtualbox
Experimental: false
Insecure Registries:
 127.0.0.0/8
Live Restore Enabled: false
```
