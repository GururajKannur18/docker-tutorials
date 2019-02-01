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
