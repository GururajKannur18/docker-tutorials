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
