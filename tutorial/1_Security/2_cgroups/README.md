## Define Memory Limits

`docker run -d --name mb100 --memory 100m alpine top`{{execute}}

`docker stats --no-stream`

## Define CPU Shares

```
docker run -d --name c768 --cpuset-cpus 0 --cpu-shares 768 benhall/cpu-stress
docker run -d --name c256 --cpuset-cpus 0 --cpu-shares 256 benhall/cpu-stress
docker stats --no-stream
docker rm -f c768 c256
```

## Use Network Namespace

`docker run -it alpine ip addr show`

`docker run -it --net=host alpine ip addr show`

## Use Pid Namespace

`docker run -it alpine ps aux`

`docker run -it --pid=host alpine ps aux`

## Sharing Processes

`docker run -d --name http nginx:alpine`

`docker run --net=container:http benhall/curl curl localhost`

_requires Docker 1.12_

`docker run --pid=container:http alpine ps aux`
