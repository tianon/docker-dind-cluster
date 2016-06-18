# Docker DinD Cluster

A simple `docker-compose.yml` to demo/test things in a _very_ simple swarm cluster (as usual for DinD, NOT RECOMMENDED FOR ANY SERIOUS USE).

```console
$ docker-compose up -d
Creating dindcluster_docker-2_1
Creating dindcluster_docker-3_1
Creating dindcluster_docker-1_1
Creating dindcluster_cluster-store_1
Creating dindcluster_swarm_1

$ export DOCKER_HOST="tcp://$(docker inspect -f '{{ (index .NetworkSettings.Networks "dindcluster_default").IPAddress }}' dindcluster_swarm_1):2375"

$ docker info
Containers: 0
...
Nodes: 3
 6f788792e52b: docker-1:2375
  └ ID: QZPY:IG6T:DUFJ:V2RQ:RWEO:H3OJ:EGI5:DOWI:MH5B:WFV4:VEUR:SDZR
  ...
 a352ad1cfede: docker-2:2375
  └ ID: YO7R:HWND:UI4Z:SXHO:URQJ:HRKA:FPNY:C3K3:MSHK:U3WT:ZUKT:N2YS
  ...
 b1b2d917aab2: docker-3:2375
  └ ID: 4CGH:23EW:UC7L:FRTP:RSKD:ARZF:6BMR:IMWG:TN7B:Y6Y5:CXKK:QCFA
  ...
Plugins: 
...

$ docker run -it --rm alpine ls -l
total 52
drwxr-xr-x    2 root     root          4096 Jun  2 19:38 bin
drwxr-xr-x    5 root     root           380 Jun 18 16:59 dev
drwxr-xr-x    1 root     root          4096 Jun 18 16:59 etc
drwxr-xr-x    2 root     root          4096 Jun  2 19:38 home
drwxr-xr-x    5 root     root          4096 Jun  2 19:38 lib
lrwxrwxrwx    1 root     root            12 Jun  2 19:38 linuxrc -> /bin/busybox
drwxr-xr-x    5 root     root          4096 Jun  2 19:38 media
drwxr-xr-x    2 root     root          4096 Jun  2 19:38 mnt
dr-xr-xr-x  256 root     root             0 Jun 18 16:59 proc
drwx------    2 root     root          4096 Jun  2 19:38 root
drwxr-xr-x    2 root     root          4096 Jun  2 19:38 run
drwxr-xr-x    2 root     root          4096 Jun  2 19:38 sbin
drwxr-xr-x    2 root     root          4096 Jun  2 19:38 srv
dr-xr-xr-x   13 root     root             0 Jun 18 16:59 sys
drwxrwxrwt    2 root     root          4096 Jun  2 19:38 tmp
drwxr-xr-x    7 root     root          4096 Jun  2 19:38 usr
drwxr-xr-x   12 root     root          4096 Jun  2 19:38 var
```
