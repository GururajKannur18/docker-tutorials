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

To try something more ambitious, you can run an Ubuntu container with: Here -t -> Terminal, -i -> interactive
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

```
$ docker rmi ubuntu:14.04
Untagged: ubuntu:14.04
Untagged: ubuntu@sha256:f961d3d101e66017fc6f0a63ecc0ff15d3e7b53b6a0ac500cd1619ded4771bd6
Deleted: sha256:f17b6a61de28594fb3ec53b1cca7164fba66357d1635b414eeed4d586744342e
Deleted: sha256:62faa9fad606573b982c0444778746244947829aa8ebefbf29b3a5291875dc84
Deleted: sha256:5848a5ca21d07333dbdf428bbdde15d5c7cecc7614b24562b49b205d8d20199a
Deleted: sha256:cd509aa64a17350b03bf6af7f41d849fc273a0f2c9d1a309e897380617fca46e
Deleted: sha256:960c7c5516b277c5c23644b2cfb53d0106543eace96d517141611fa34e1b957c
```

```
docker run -d -P seqvence/static-site
Unable to find image 'seqvence/static-site:latest' locally
latest: Pulling from seqvence/static-site

fdd5d7827f33: Downloading [=======>                                           ] 7.318 MB/51.37 MB
fdd5d7827f33: Pull complete
a3ed95caeb02: Pull complete
716f7a5f3082: Pull complete
7b10f03a0309: Pull complete
aff3ab7e9c39: Pull complete
Digest: sha256:41b286105f913fb7a5fbdce28d48bc80f1c77e3c4ce1b8280f28129ae0e94e9e
Status: Downloaded newer image for seqvence/static-site:latest
e9da3f71a2065765e6a8e11cb85f6d4c8ed1868d75e77f58459558f840157f47

```
```
docker ps
CONTAINER ID        IMAGE                  COMMAND                  CREATED              STATUS              PORTS                                           NAMES
e9da3f71a206        seqvence/static-site   "/bin/sh -c 'cd /usr/"   About a minute ago   Up About a minute   0.0.0.0:32769->80/tcp, 0.0.0.0:32768->443/tcp   focused_noyce

```

```
http://ech-10-157-136-3:32769/
```

-------------------------------------------------------------------------------------------------------------------------------


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

# This is very cool
(Note: Make sure ubuntu latest image present in docker container)
```
$ docker run -it --name temp ubuntu:latest /bin/bash
root@4abe96b094af:/#
```
Note - Press Ctrl + P + Q get out of this


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

# Setup Redis
```
$ docker pull redis
Using default tag: latest
latest: Pulling from library/redis
a5a6f2f73cd8: Pull complete
a6d0f7688756: Pull complete
53e16f6135a5: Pull complete
f52b0cc4e76a: Pull complete
e841feee049e: Pull complete
ccf45e5191d0: Pull complete
Digest: sha256:010a8bd5c6a9d469441aa35187d18c181e3195368bce309348b3ee639fce96e0
Status: Downloaded newer image for redis:latest

$ docker run --name some-redis -d redis
9c309a278d2f2ddafc5b9f355dde74055781619d7323ea8f3125106faaff32c2

$ docker exec -it some-redis redis-cli
127.0.0.1:6379>
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


# Docker Swarm

# Containers Vs VM

Docker containers are just isolated system environment run with the same kernel as host.

# Docker Objects
1) Images - Like VM, container image is template for containers. They consist mostly of file system, but also metadata about the container including how we should operate by default.

- sharing image using docker commands
- Docker manages images on host gives you the tools to transport them across host. Usually by registries.

2) Containers - are instances of images, basically copies then isolated process inside them. To the process it looks as if it has own system based on the file system of image. They can change the file system but any changes have to be committed back to an image to persist.

- Docker manages images like processes - meaning you can start, stop and run in the background, run interactively etc..

3) Dockerfiles - are build files that instructs docker how to consistently configure container images.

4) Registries - serve images you can pull from & push into from docker. Docker index is considered main public registry. 

Layered - Copy on Write Filesystem
- Content Layer
- init layer

uses layer copy on write FS (File System) i.e., file you see on container when it start are actually file images in the system until changes are made.

Changes made in the container are collectively make up a layer & can be committed to an image. Images are just collection of layers on file system changes. This allows docker efficient with the disk space, also registries are important. Since they're aware about layers and cannot send layers, you dont have when you pull in images.

Containers are not just file systems, they run using commands. This command run in process isolation using namespace and 'C' groups.

```
[dc-user@ech-10-157-136-3 ~]$ docker run -it ubuntu:latest bash
Unable to find image 'ubuntu:latest' locally
latest: Pulling from library/ubuntu

38e2e6cd5626: Pull complete
705054bc3f5b: Pull complete
c7051e069564: Pull complete
7308e914506c: Pull complete
Digest: sha256:945039273a7b927869a07b375dc3148de16865de44dec8398672977e050a072e
Status: Downloaded newer image for ubuntu:latest

root@25f13c4f1816:/# cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=18.04
DISTRIB_CODENAME=bionic
DISTRIB_DESCRIPTION="Ubuntu 18.04.1 LTS"
root@25f13c4f1816:/#
root@25f13c4f1816:/# exit
exit
```

```
[dc-user@ech-10-157-136-3 ~]$ docker ps -l --format=$FORMAT
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS                      PORTS               NAMES
6a66709a8a05        ubuntu:latest       "bash"              4 minutes ago       Exited (0) 24 seconds ago                       clever_davinci
```

```
[dc-user@ech-10-157-136-3 ~]$ docker ps
CONTAINER ID        IMAGE                  COMMAND                  CREATED             STATUS              PORTS                                           NAMES
e9da3f71a206        seqvence/static-site   "/bin/sh -c 'cd /usr/"   6 weeks ago         Up 6 weeks          0.0.0.0:32769->80/tcp, 0.0.0.0:32768->443/tcp   focused_noyce
```

create the file 
touch MY_FILE

```
[dc-user@ech-10-157-136-3 ~]$ docker commit a25b4e978628
sha256:d55cf549af410b694697f812829d5cf41fbf32bf5f410c5babe9df86686270a2
```

```
[dc-user@ech-10-157-136-3 ~]$ docker images
REPOSITORY                             TAG                 IMAGE ID            CREATED             SIZE
my-new-image                           latest              d55cf549af41        2 minutes ago       87.47 MB
ubuntu                                 latest              20bb25d32758        8 days ago          87.47 MB
[dc-user@ech-10-157-136-3 ~]$
```

```
docker run -ti my-new-image bash
root@b2845052a960:/# ls
MY_FILE  bin  boot  dev  etc  home  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
root@b2845052a960:/#
```

```
[dc-user@ech-10-157-136-3 ~]$ docker container ls
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
```

```
[dc-user@ech-10-157-136-3 ~]$ DOCKER_HIDE_LEGACY_COMMANDS=true docker --help

Usage:  docker COMMAND

A self-sufficient runtime for containers

Options:
      --config string      Location of client config files (default "/home/dc-user/.docker")
  -D, --debug              Enable debug mode
      --help               Print usage
  -H, --host list          Daemon socket(s) to connect to
  -l, --log-level string   Set the logging level ("debug"|"info"|"warn"|"error"|"fatal") (default "info")
      --tls                Use TLS; implied by --tlsverify
      --tlscacert string   Trust certs signed only by this CA (default "/home/dc-user/.docker/ca.pem")
      --tlscert string     Path to TLS certificate file (default "/home/dc-user/.docker/cert.pem")
      --tlskey string      Path to TLS key file (default "/home/dc-user/.docker/key.pem")
      --tlsverify          Use TLS and verify the remote
  -v, --version            Print version information and quit

Management Commands:
  container   Manage containers
  image       Manage images
  network     Manage networks
  node        Manage Swarm nodes
  plugin      Manage plugins
  secret      Manage Docker secrets
  service     Manage services
  stack       Manage Docker stacks
  swarm       Manage Swarm
  system      Manage Docker
  volume      Manage volumes

Commands:
  build       Build an image from a Dockerfile
  login       Log in to a Docker registry
  logout      Log out from a Docker registry
  run         Run a command in a new container
  search      Search the Docker Hub for images
  version     Show the Docker version information

Run 'docker COMMAND --help' for more information on a command.
[dc-user@ech-10-157-136-3 ~]$
```

```
[dc-user@ech-10-157-136-3 ~]$ docker container --help

Usage:  docker container COMMAND

Manage containers

Options:
      --help   Print usage

Commands:
  attach      Attach local standard input, output, and error streams to a running container
  commit      Create a new image from a container's changes
  cp          Copy files/folders between a container and the local filesystem
  create      Create a new container
  diff        Inspect changes to files or directories on a container's filesystem
  exec        Run a command in a running container
  export      Export a container's filesystem as a tar archive
  inspect     Display detailed information on one or more containers
  kill        Kill one or more running containers
  logs        Fetch the logs of a container
  ls          List containers
  pause       Pause all processes within one or more containers
  port        List port mappings or a specific mapping for the container
  prune       Remove all stopped containers
  rename      Rename a container
  restart     Restart one or more containers
  rm          Remove one or more containers
  run         Run a command in a new container
  start       Start one or more stopped containers
  stats       Display a live stream of container(s) resource usage statistics
  stop        Stop one or more running containers
  top         Display the running processes of a container
  unpause     Unpause all processes within one or more containers
  update      Update configuration of one or more containers
  wait        Block until one or more containers stop, then print their exit codes

Run 'docker container COMMAND --help' for more information on a command.
```

```
[dc-user@ech-10-157-136-3 ~]$ docker container run --help
```

```
docker container run -it jboss/wildfly
```

```
[dc-user@ech-10-157-136-3 ~]$ docker container run -d jboss/wildfly
6f7a0d1d83efdc1929c12c83986a0861c94422dc8d86862114dd33f9896eda16
```

```
[dc-user@ech-10-157-136-3 ~]$ docker container ls
CONTAINER ID        IMAGE               COMMAND                  CREATED              STATUS              PORTS               NAMES
6f7a0d1d83ef        jboss/wildfly       "/opt/jboss/wildfl..."   20 seconds ago       Up 19 seconds       8080/tcp            sleepy_euclid
9bc9a8210f1c        jboss/wildfly       "/opt/jboss/wildfl..."   43 seconds ago       Up 41 seconds       8080/tcp            priceless_rosalind
c27b1024702a        jboss/wildfly       "/opt/jboss/wildfl..."   About a minute ago   Up About a minute   8080/tcp            priceless_wright
```

```
[dc-user@ech-10-157-136-3 ~]$ docker container stop 6f7a0d1d83ef 9bc9a8210f1c c27b1024702a
6f7a0d1d83ef
9bc9a8210f1c
c27b1024702a
```

```
[dc-user@ech-10-157-136-3 ~]$ docker container ls
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
```

```
[dc-user@ech-10-157-136-3 ~]$ docker container ls -a
CONTAINER ID        IMAGE                                  COMMAND                  CREATED             STATUS                          PORTS               NAMES
6f7a0d1d83ef        jboss/wildfly                          "/opt/jboss/wildfl..."   2 minutes ago       Exited (0) About a minute ago                       sleepy_euclid
9bc9a8210f1c        jboss/wildfly                          "/opt/jboss/wildfl..."   3 minutes ago       Exited (0) About a minute ago                       priceless_rosalind
0d8aaa7e04b1        jboss/wildfly                          "/opt/jboss/wildfl..."   4 minutes ago       Exited (0) 3 minutes ago                            vibrant_leakey
c27b1024702a        jboss/wildfly                          "/opt/jboss/wildfl..."   4 minutes ago       Exited (0) About a minute ago                       priceless_wright
b9a7008bd9ae        jboss/wildfly                          "/opt/jboss/wildfl..."   7 minutes ago       Exited (0) 5 minutes ago                            naughty_roentgen
68ab6fe6266d        ubuntu:latest                          "bash"                   20 hours ago        Exited (0) 20 hours ago                             cocky_mclean
6a66709a8a05        ubuntu:latest                          "bash"                   22 hours ago        Exited (0) 21 hours ago                             clever_davinci
b2845052a960        my-new-image                           "bash"                   22 hours ago        Exited (0) 22 hours ago                             elated_tesla
d5ac72cbe5ba        my-image                               "bash"                   22 hours ago        Exited (0) 22 hours ago                             jolly_bassi
68393fa94b79        ubuntu:latest                          "bash"                   22 hours ago        Exited (0) 22 hours ago                             compassionate_lumiere
36037204973b        ubuntu:latest                          "bash"                   22 hours ago        Exited (0) 22 hours ago                             jolly_hugle
ddd5b5dfbdbf        ubuntu:latest                          "bash"                   22 hours ago        Exited (0) About an hour ago                        small_darwin
a25b4e978628        ubuntu:latest                          "bash"                   24 hours ago        Exited (0) 24 hours ago                             jovial_payne
a2f8935a71fb        ubuntu:latest                          "bash"                   24 hours ago        Exited (0) 22 hours ago                             pensive_mayer
25f13c4f1816        ubuntu:latest                          "bash"                   24 hours ago        Exited (0) 24 hours ago                             clever_bartik
e9da3f71a206        seqvence/static-site                   "/bin/sh -c 'cd /u..."   6 weeks ago         Exited (0) About an hour ago                        focused_noyce
5d2c2fce2d95        kbastani/hystrix-dashboard             "java -Djava.secur..."   6 weeks ago         Exited (0) 6 weeks ago                              docker_hystrix_1
9355865d9a72        kbastani/api-gateway-microservice      "java -Djava.secur..."   6 weeks ago         Exited (0) 6 weeks ago                              docker_gateway_1
f16762e202fe        kbastani/recommendation-microservice   "java -Djava.secur..."   6 weeks ago         Exited (0) 6 weeks ago                              docker_recommendation_1
e5b93365939f        kbastani/movies-ui                     "java -Djava.secur..."   6 weeks ago         Exited (0) 6 weeks ago                              docker_moviesui_1
4d750d4b602e        kbastani/users-microservice            "java -Djava.secur..."   6 weeks ago         Exited (0) 6 weeks ago                              docker_user_1
3062842547fa        kbastani/movie-microservice            "java -Djava.secur..."   6 weeks ago         Exited (0) 6 weeks ago                              docker_movie_1
d7ed201425b3        kbastani/config-microservice           "java -Djava.secur..."   6 weeks ago         Exited (0) 6 weeks ago                              docker_configserver_1
f9a10b7c0d0a        kbastani/discovery-microservice        "java -Djava.secur..."   6 weeks ago         Exited (0) 6 weeks ago                              docker_discovery_1
b132a4059228        c49319bd6912                           "sh -c 'java $JAVA..."   8 weeks ago         Exited (0) 8 weeks ago                              sad_joliot
2b8dd116ad20        c49319bd6912                           "sh -c 'java $JAVA..."   8 weeks ago         Created                                             sleepy_hoover
51fef35f4ad4        c49319bd6912                           "sh -c 'java $JAVA..."   8 weeks ago         Exited (0) 8 weeks ago                              jolly_raman
d2ea8a77ba54        redis                                  "docker-entrypoint..."   2 months ago        Exited (0) 2 months ago                             some-redis
1be4f5dde2fb        a02eab9e2434                           "/entrypoint.sh my..."   2 months ago        Exited (0) 2 months ago                             mysql
0f9abac69c0a        f991c20cb508                           "docker-entrypoint..."   2 months ago        Exited (0) 2 months ago                             stoic_cray
f903d1f31bae        4ab4c602aa5e                           "/hello"                 2 months ago        Exited (0) 2 months ago                             hopeful_sammet
4b4685bedbee        redis                                  "docker-entrypoint..."   2 months ago        Exited (0) 2 months ago                             peaceful_dubinsky
9ab08df5606e        f991c20cb508                           "docker-entrypoint..."   2 months ago        Exited (0) 2 months ago                             tiny_varahamihira
ef7630c911c8        4ab4c602aa5e                           "/hello"                 2 months ago        Exited (0) 2 months ago                             backstabbing_lalande
e7d9e3713f5c        93fd78260bd1                           "/bin/bash"              2 months ago        Exited (0) 2 months ago                             angry_hodgkin
970c680f4fa6        93fd78260bd1                           "/bin/bash"              2 months ago        Exited (0) 2 months ago                             mad_goldstine
5ca8716abba8        97319b0b7d17                           "ruby hello.rb"          2 months ago        Exited (0) 2 months ago                             modest_chandrasekhar
50e4e8c9923f        ec347d11e305                           "echo 'Hello O'Rei..."   2 months ago        Exited (0) 2 months ago                             boring_bartik
6f2025730fff        c54a2cc56cbb                           "/hello"                 2 years ago         Exited (0) 2 years ago                              amazing_lumiere
```


# assign the name relevant to my application
```
docker container run -d --name web jboss/wildfly
2019f12e23c71d5076eea22e3ee79d4655be47d0a7b8c046bc6b0ae6340dc96d
```

```
docker container ls -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS               NAMES
2019f12e23c7        jboss/wildfly       "/opt/jboss/wildfl..."   18 seconds ago      Up 16 seconds       8080/tcp            web
```

# Stop the container and remove it (single command -f --> stops and removes)
```
docker container rm -f web
web
```

# If I want to run the shell in the container:
Note: -it -> Interactive way we can see logs on the shell...but -d (detached mode), we can see only long id.
```
[dc-user@ech-10-157-136-3 ~]$ docker container run -it --name web jboss/wildfly bash
[jboss@e5226e05529f ~]$ ls
wildfly
[jboss@e5226e05529f ~]$ cd wildfly/
[jboss@e5226e05529f wildfly]$ pwd
/opt/jboss/wildfly
[jboss@e5226e05529f wildfly]$ ls
LICENSE.txt  README.txt  appclient  bin  copyright.txt  docs  domain  jboss-modules.jar  modules  standalone  welcome-content
[jboss@e5226e05529f wildfly]$ cd standalone/
[jboss@e5226e05529f standalone]$ ls -la
total 8
drwxrwxr-x  6 jboss root   64 Jan  5 19:10 .
drwxrwxr-x 12 jboss root 4096 Jan  5 19:10 ..
drwxrwxr-x  2 jboss root 4096 Jan 11 09:19 configuration
drwxrwxr-x  2 jboss root   23 Jan 11 09:19 deployments
drwxrwxr-x  3 jboss root   16 Jan  5 19:10 lib
drwxrwxr-x  3 jboss root   17 Jan  5 19:10 tmp
[jboss@e5226e05529f standalone]$ exit
exit
[dc-user@ech-10-157-136-3 ~]$
```

# Run container(ports and volumes)
Note: -P which says take all exposed ports & published them in pre-defined range 
	  -p take port 8080 on the host and map it to port

```
docker container run -d --name web -P jboss/wildfly
ea9ac53dcc4f8b33b859fe8a99b49722a97496a5f8bdee728c89ddf4a8120735
```

```
docker container ls
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                     NAMES
ea9ac53dcc4f        jboss/wildfly       "/opt/jboss/wildfl..."   36 seconds ago      Up 35 seconds       0.0.0.0:32768->8080/tcp   web
```

Note - ``0.0.0.0:32768->8080/tcp``, take all the network interfaces on the host which is indicated by 0.0.0.0 port 32768 over there and reidirect it to port 8080 in the container

Access the link: http://10.157.136.3:32768/

# If I want to see the logs of docker container
```
docker container logs web
```

```
# stop the docker container
docker container stop web
web
```

```
# Remove container 
docker container rm web
web
```

```
docker container run -d --name web -p 8080:8080 jboss/wildfly
```

Now, access the link: http://10.157.136.3:8080/

Note: Go to the location where sample.war file present and then execute the following commands:

```
docker container run -d --name web -p 8080:8080 -v `pwd`/webapp.war:/opt/jboss/wildfly/standalone/deployments/webapp.war jboss/wildfly
c4bd4393b395f336a4a5e544b9c5ac29628c6953a5d18f6d3084eda91f581501
```

# see the logs
```
docker container logs web
```

# we can also tail the logs:
```
docker container logs web -f 
```

```
curl http://localhost:8080/webapp/resources/persons
<?xml version="1.0" encoding="UTF-8" standalone="yes"?><collection><person><name>Penny</name></person><person><name>Leonard</name></person><person><name>Sheldon</name></person><person><name>Amy</name></person><person><name>Howard</name></person><person><name>Bernadette</name></person><person><name>Raj</name></person><person><name>Priya</name></person></collection>
```

# From Browser:
```
http://10.157.136.3:8080/webapp/resources/persons
```


# Create your first java docker image
Note: -t - tags
      . means build context 
      
Dockerfile
```
FROM openjdk:jdk-alpine

CMD java -version
```


```
docker image build -t hellojava .
Sending build context to Docker daemon  2.048kB
Step 1/2 : FROM openjdk
latest: Pulling from library/openjdk
ab1fc7e4bf91: Pull complete
35fba333ff52: Pull complete
f0cb1fa13079: Pull complete
3d1dd648b5ad: Pull complete
a9f886e483d6: Pull complete
f0c295b9cf6e: Pull complete
afe560095725: Pull complete
dc8253cd29cd: Pull complete
6885295983c8: Pull complete
Digest: sha256:761a6053925601d420754753cfce5b5527478991f30ae21a49cfac019323935d
Status: Downloaded newer image for openjdk:latest
 ---> 2cbfaac94298
Step 2/2 : CMD java -version
 ---> Running in c892a4ce2a8e
 ---> 920a2b72ca8a
Removing intermediate container c892a4ce2a8e
Successfully built 920a2b72ca8a
Successfully tagged hellojava:latest
```

```
docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
hellojava           latest              0bf7bff6fed1        18 seconds ago      821MB
openjdk             latest              2cbfaac94298        9 days ago          821MB
```
```
docker container run hellojava
openjdk version "11.0.1" 2018-10-16
OpenJDK Runtime Environment (build 11.0.1+13-Debian-2bpo91)
OpenJDK 64-Bit Server VM (build 11.0.1+13-Debian-2bpo91, mixed mode, sharing)
```

```
docker image build -t hellojava:2 .
Sending build context to Docker daemon  2.048kB
Step 1/2 : FROM openjdk:jdk-alpine
jdk-alpine: Pulling from library/openjdk
8e3ba11ec2a2: Pull complete
311ad0da4533: Pull complete
df312c74ce16: Pull complete
Digest: sha256:1fd5a77d82536c88486e526da26ae79b6cd8a14006eb3da3a25eb8d2d682ccd6
Status: Downloaded newer image for openjdk:jdk-alpine
 ---> 5801f7d008e5
Step 2/2 : CMD java -version
 ---> Running in 865e514a63ad
 ---> 5e0a037757fb
Removing intermediate container 865e514a63ad
Successfully built 5e0a037757fb
Successfully tagged hellojava:2
```

```
docker image ls
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
hellojava           2                   5e0a037757fb        19 seconds ago      103MB
hellojava           latest              0bf7bff6fed1        5 minutes ago       821MB
openjdk             latest              2cbfaac94298        9 days ago          821MB
openjdk             jdk-alpine          5801f7d008e5        6 months ago        103MB
```
```
docker container run hellojava:2
openjdk version "1.8.0_171"
OpenJDK Runtime Environment (IcedTea 3.8.0) (Alpine 8.171.11-r0)
OpenJDK 64-Bit Server VM (build 25.171-b11, mixed mode)
```

# Copy Files in the docker image

- COPY instructions: Copy new files or directories to the container filesystem
- ADD instructions: 
	COPY instructions
	Allow tar file auto-extraction in the image
	- For ex: ADD app.tar.gz /opt/var/myapp
	Can download files from remote URL
	- Recommanded to use CURL or wget instead
	
Dockerfile
```
FROM jboss/wildfly

COPY webapp.war /opt/jboss/wildfly/standalone/deployments/webapp.war
```

```	
docker image build -t helloweb .
Sending build context to Docker daemon  9.216kB
Step 1/2 : FROM jboss/wildfly
latest: Pulling from jboss/wildfly
aeb7866da422: Pull complete
157601a0b538: Pull complete
642f4164f381: Pull complete
bda512e97517: Pull complete
4cccaafdae21: Pull complete
Digest: sha256:310dabba2d67c98a22fd8f2e51fcb8575d3071737159a75e7edd5182b505dfff
Status: Downloaded newer image for jboss/wildfly:latest
 ---> 2602b4852593
Step 2/2 : COPY webapp.war /opt/jboss/wildfly/standalone/deployments/webapp.war
 ---> 6ab53ec1a8c9
Removing intermediate container cdfc09926e98
Successfully built 6ab53ec1a8c9
Successfully tagged helloweb:latest
```
```
docker container run -p 8080:8080 -d helloweb
d65f1c6b79828c17fbe2a720259d0b4708bae10aad97b715941f5d26ddfc7026
```
```
docker container ls
CONTAINER ID        IMAGE               COMMAND                  CREATED              STATUS              PORTS                    NAMES
d65f1c6b7982        helloweb            "/opt/jboss/wildfl..."   About a minute ago   Up About a minute   0.0.0.0:8080->8080/tcp   determined_easley
```

```
curl http://localhost:8080/webapp/resources/persons
<?xml version="1.0" encoding="UTF-8" standalone="yes"?><collection><person><name>Penny</name></person><person><name>Leonard</name></person><person><name>Sheldon</name></person><person><name>Amy</name></person><person><name>Howard</name></person><person><name>Bernadette</name></person><person><name>Raj</name></person><person><name>Priya</name></person></collection>
```

# Run JAR files from the docker

Goto the chapter2, create Dockerfile

```
FROM openjdk:jdk-alpine

COPY myapp/target/myapp-1.0-SNAPSHOT.jar /deployments/

CMD java -jar /deployments/myapp-1.0-SNAPSHOT.jar
```

Now, go to the myapp directory and  >mvn clean install -DskipTests
Note: Make sure the myapp-1.0-SNAPSHOT.jar is created there.

```
docker build -t hellojava:3 .
Sending build context to Docker daemon   55.3kB
Step 1/3 : FROM openjdk:jdk-alpine
 ---> 5801f7d008e5
Step 2/3 : COPY myapp/target/myapp-1.0-SNAPSHOT.jar /deployments/
 ---> 6ab779dff505
Removing intermediate container c505ed53daae
Step 3/3 : CMD java -jar /deployments/myapp-1.0-SNAPSHOT.jar
 ---> Running in 0f4c47edb022
 ---> 841cbd40188d
Removing intermediate container 0f4c47edb022
Successfully built 841cbd40188d
Successfully tagged hellojava:3
```

```
docker image ls
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
hellojava           3                   841cbd40188d        2 minutes ago       103MB
helloweb            latest              6ab53ec1a8c9        14 minutes ago      675MB
hellojava           2                   5e0a037757fb        40 minutes ago      103MB
hellojava           latest              0bf7bff6fed1        45 minutes ago      821MB
openjdk             latest              2cbfaac94298        9 days ago          821MB
jboss/wildfly       latest              2602b4852593        3 weeks ago         675MB
openjdk             jdk-alpine          5801f7d008e5        6 months ago        103MB
```

docker container run hellojava:3
Hello World!


# How to repacage and rebuild the application??
Change the syso statement, build the maven project using >mvn clean install -DskipTests and again package the image

```
docker build -t hellojava:4 .
Sending build context to Docker daemon   55.3kB
Step 1/3 : FROM openjdk:jdk-alpine
 ---> 5801f7d008e5
Step 2/3 : COPY myapp/target/myapp-1.0-SNAPSHOT.jar /deployments/
 ---> b315a06e9573
Removing intermediate container bdeaa1c29b26
Step 3/3 : CMD java -jar /deployments/myapp-1.0-SNAPSHOT.jar
 ---> Running in 90ee32aff31c
 ---> b494d9535490
Removing intermediate container 90ee32aff31c
Successfully built b494d9535490
Successfully tagged hellojava:4
```

```
docker image ls
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
hellojava           4                   b494d9535490        28 seconds ago      103MB
hellojava           3                   841cbd40188d        7 minutes ago       103MB
helloweb            latest              6ab53ec1a8c9        19 minutes ago      675MB
hellojava           2                   5e0a037757fb        45 minutes ago      103MB
hellojava           latest              0bf7bff6fed1        About an hour ago   821MB
openjdk             latest              2cbfaac94298        9 days ago          821MB
jboss/wildfly       latest              2602b4852593        3 weeks ago         675MB
openjdk             jdk-alpine          5801f7d008e5        6 months ago        103MB
```

```
docker container run hellojava:4
Howdy World!

docker container run hellojava:3
Hello World!
```

# Other Docker instructions

# RUN and CMD
- RUN: used for installing software package
	RUN apt-get update && apt-get install -y git
	RUN /opt/jboss/wildfly/bin/add-user.sh admin Admin#007 -silent
	
- CMD: defaults for executing container; can be overriden from CLI 
	CMD ["/opt/jboss/wildfly/bin/standalone.sh", "-b", "0.0.0.0", "-bmanagement", "0.0.0.0"]
	docker run mywildfly bash
	
- ENTRYPOINT: configures the container executable; can be overridden using --entrypoint from CLI
	Default value: /bin/sh -c
	ENTRYPOINT ["/entrypoint.sh"]
	
# Expose and Volume

- EXPOSE: network ports on which the container is listening 
For ex: EXPOSE 9990
Need to explicily publish the host port 

- VOLUME: creates a mount point with the specified name
	VOLUME /opt/couchbase/var 
	docker container run ... -v ~/data:/opt/couchbase/var
	
	
# USER and HEALTHCHECK
- USER : sets the user name or UID to use when running the image 

- HEALTHCHECK: performs a healthcheck on the application inside the container
	HEALTHCHECK --interval=5s --timeout=3s CMD curl --fail http://localhost:8091/pools || exit 1

------------------------------------------------------

``docker-java-sample`` - download this from https://github.com/arun-gupta/docker-java-sample


# Docker and Maven 
- Packaging and running the java application exclusively with Docker requires hard coding 
- Typical java workflow includes Maven and other tools
- Maven plugins available for Docker

```
mvn package -Pdocker
```
```
docker image ls
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
hellojava           latest              006b6c0ea07b        11 seconds ago      821MB
```
```
mvn install -Pdocker
```


# Tag and Share Docker Images

# Instead of using the above hack from old days you can use now:
```
docker image prune -a
```

```
docker container ls -aq
d65f1c6b7982
```
```
docker container rm -f $(docker container ls -aq)
d65f1c6b7982
```

```
docker image build  .
Sending build context to Docker daemon  2.048kB
Step 1/2 : FROM openjdk:jdk-alpine
jdk-alpine: Pulling from library/openjdk
8e3ba11ec2a2: Pull complete
311ad0da4533: Pull complete
df312c74ce16: Pull complete
Digest: sha256:1fd5a77d82536c88486e526da26ae79b6cd8a14006eb3da3a25eb8d2d682ccd6
Status: Downloaded newer image for openjdk:jdk-alpine
 ---> 5801f7d008e5
Step 2/2 : CMD echo "This is v1"
 ---> Running in c3292404af9b
 ---> a5d71ef27da8
Removing intermediate container c3292404af9b
Successfully built a5d71ef27da8
```

```
docker image ls
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
<none>              <none>              a5d71ef27da8        33 seconds ago      103MB
openjdk             jdk-alpine          5801f7d008e5        6 months ago        103MB
```
# Without TAG and REPOSITORY, run the container by IMAGE ID
```
docker container run a5d71ef27da8
This is v1
```
```
docker image build -t helloworld .
Sending build context to Docker daemon  2.048kB
Step 1/2 : FROM openjdk:jdk-alpine
 ---> 5801f7d008e5
Step 2/2 : CMD echo "This is v1"
 ---> Using cache
 ---> a5d71ef27da8
Successfully built a5d71ef27da8
Successfully tagged helloworld:latest
```

```
docker image ls
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
helloworld          latest              a5d71ef27da8        3 minutes ago       103MB
openjdk             jdk-alpine          5801f7d008e5        6 months ago        103MB
```

```
docker container run helloworld
This is v1
docker container run helloworld:latest
This is v1
```
# Now I'm going to remove the images with the latest tag
```
docker image rm helloworld:latest
Error response from daemon: conflict: unable to remove repository reference "helloworld:latest" (must force) - container a41572d49e45 is using its referenced image a5d71ef27da8

docker container ls -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS                      PORTS               NAMES
173f5c83b67a        helloworld:latest   "/bin/sh -c 'echo ..."   50 seconds ago      Exited (0) 49 seconds ago                       wizardly_heisenberg
1a5c5040bc06        helloworld:latest   "/bin/sh -c 'echo ..."   52 seconds ago      Exited (0) 51 seconds ago                       upbeat_beaver
a41572d49e45        helloworld:latest   "/bin/sh -c 'echo ..."   56 seconds ago      Exited (0) 55 seconds ago                       elegant_beaver
```

```
docker container rm -f $(docker container ls -aq)
173f5c83b67a
1a5c5040bc06
a41572d49e45

docker image rm helloworld:latest
Untagged: helloworld:latest
Deleted: sha256:a5d71ef27da87f3407e228f6c90fd21c367ad0f662b399d6480499d619d23cbb

docker image build -t hellowold:1 .
Sending build context to Docker daemon  2.048kB
Step 1/2 : FROM openjdk:jdk-alpine
 ---> 5801f7d008e5
Step 2/2 : CMD echo "This is v1"
 ---> Running in e1ada4cd2c31
 ---> e05dccba3986
Removing intermediate container e1ada4cd2c31
Successfully built e05dccba3986
Successfully tagged hellowold:1

docker image ls
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
hellowold           1                   e05dccba3986        28 seconds ago      103MB
openjdk             jdk-alpine          5801f7d008e5        6 months ago        103MB

docker container run hellowold:1
This is v1

# How to tag the image ??
docker image tag hellowold:1 hellowold:latest

docker image ls
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
hellowold           1                   e05dccba3986        3 minutes ago       103MB
hellowold           latest              e05dccba3986        3 minutes ago       103MB
openjdk             jdk-alpine          5801f7d008e5        6 months ago        103MB

docker container run hellowold:latest
This is v1

# Now open Dockerfile and change echo statement
docker image build -t hellowold:2 .
Sending build context to Docker daemon  2.048kB
Step 1/2 : FROM openjdk:jdk-alpine
 ---> 5801f7d008e5
Step 2/2 : CMD echo "This is v2"
 ---> Running in f65948a9e30b
 ---> 204a942b1a38
Removing intermediate container f65948a9e30b
Successfully built 204a942b1a38
Successfully tagged hellowold:2


# This still shows v1
docker container run hellowold
This is v1


docker image ls
REPOSITORY          TAG                 IMAGE ID            CREATED              SIZE
hellowold           2                   204a942b1a38        About a minute ago   103MB
hellowold           1                   e05dccba3986        6 minutes ago        103MB
hellowold           latest              e05dccba3986        6 minutes ago        103MB
openjdk             jdk-alpine          5801f7d008e5        6 months ago         103MB


docker image tag hellowold:2 hellowold:latest
docker image ls
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
hellowold           2                   204a942b1a38        2 minutes ago       103MB
hellowold           latest              204a942b1a38        2 minutes ago       103MB
hellowold           1                   e05dccba3986        7 minutes ago       103MB
openjdk             jdk-alpine          5801f7d008e5        6 months ago        103MB
[dc-user@ech-10-157-136-3 helloworld]$ docker container run hellowold
This is v2

docker image tag hellowold:2 prateekashtikar/hellowold:latest

docker login
Login with your Docker ID to push and pull images from Docker Hub. If you don't have a Docker ID, head over to https://hub.docker.com to create one.
Username: prateek512
Password:
Login Succeeded

docker run -d -p 5000:5000 --restart always --name registry registry:2.6.0
Unable to find image 'registry:2.6.0' locally
2.6.0: Pulling from library/registry
709515475419: Pull complete
df6e278d8f96: Pull complete
16218e264e88: Pull complete
16748da81f63: Pull complete
8d73e673c34c: Pull complete
Digest: sha256:28be0609f90ef53e86e1872a11d672434ce1361711760cf1fe059efd222f8d37
Status: Downloaded newer image for registry:2.6.0
a24c2575c60d1556740ac5bba9bb201ef315afa3b79c120ec0b53ddb1b906257


docker image tag hellowold:latest localhost:5000/prateeashtikar/helloworld:latest

docker image ls
REPOSITORY                                 TAG                 IMAGE ID            CREATED             SIZE
prateekashtikar/hellowold                  latest              204a942b1a38        31 minutes ago      103MB
localhost:5000/prateeashtikar/helloworld   latest              204a942b1a38        31 minutes ago      103MB
hellowold                                  2                   204a942b1a38        31 minutes ago      103MB
hellowold                                  latest              204a942b1a38        31 minutes ago      103MB
hellowold                                  1                   e05dccba3986        37 minutes ago      103MB
openjdk                                    jdk-alpine          5801f7d008e5        6 months ago        103MB
registry                                   2.6.0               047218491f8c        23 months ago       33.2MB

docker image push localhost:5000/prateeashtikar/helloworld:latest
The push refers to a repository [localhost:5000/prateeashtikar/helloworld]
93351e248e6e: Pushed
298c3bb2664f: Pushed
73046094a9b8: Pushed
latest: digest: sha256:20d4e51eee3be4afea1a83867194b2728b5efd538bbbea66fc86b97d3c382a1e size: 947
```


```
docker run -d -p 5000:5000 --restart always --name regsitry registry:2.6.0
Unable to find image 'registry:2.6.0' locally
2.6.0: Pulling from library/registry
709515475419: Pull complete
df6e278d8f96: Pull complete
16218e264e88: Pull complete
16748da81f63: Pull complete
8d73e673c34c: Pull complete
Digest: sha256:28be0609f90ef53e86e1872a11d672434ce1361711760cf1fe059efd222f8d37
Status: Downloaded newer image for registry:2.6.0
863df0930b73beb2674138a6e8413fdb2ef3596a6cbc335815aaa1e40955cd39
```

Now, push image to local registry tag image here

```
docker image push localhost:5000/prateek512/helloworld
The push refers to repository [localhost:5000/prateek512/helloworld]
4b7d93055d87: Pushed
663e8522d78b: Pushed
283fb404ea94: Pushed
bebe7ce6215a: Pushed
latest: digest: sha256:f15b6bc7cf40b72c6c6602d56f5de05fd093e0e282da151b95e02fd5b03ff46b size: 1150
```







