# Docker Ops

## 1. Manage Images

Display Local Images
```
docker images
```

Delete Images
```
# delete local images
docker rmi [image ID]
docker rmi [repo:tag]
# delete all untagged images
docker rmi $(docker images | grep "^<none>" | awk "{print $3}")
```

Run images
```
> -v: mount folder
docker run -d -P -v /myvolume ng

> -p: map port
docker run -d -p 8080:80 nginx:1.7

> -P: auto map port
docker run -d -P nginx:1.7
docker run -i -t -v /data/src:/test/src nginx:1.7
```

## 2. Manage Containers [^1]

List containers
```
docker ps
```

Start one or more stopped containers
```
docker start [OPTIONS] CONTAINER [CONTAINER...]
docker start 74e0f6c5fa0d
```

Stop a running container
```
# by sending SIGTERM
# and then SIGKILL after a grace period
docker stop [OPTIONS] CONTAINER [CONTAINER...]
docker stop 74e0f6c5fa0d
```

Remove containers
```
> remove one or more containers
docker rm [OPTIONS] CONTAINER [CONTAINER...]
docker rm 74e0f6c5fa0d
> remove all container
docker ps -q -a | xargs docker rm -f
```

Run container
```
# run a command in a running container
# start another process within a container
docker exec [OPTIONS] CONTAINER COMMAND [ARG...]
docker exec -it 74e0f6c5fa0d bash
```

Detach the container without exiting the shell
```
Ctrl-p + Ctrl-q
```

## Debugging and Monitoring

**Logging**

```
# fetch the logs of a container
docker logs -f CONTAINER

# options
  -f, --follow=false        Follow log output
  --help=false              Print usage
  --since=                  Show logs since timestamp
  -t, --timestamps=false    Show timestamps
  --tail=all                Number of lines to show from the end of the logs
```

**Networks** [^3]

```
ip a | grep docker
brctl docker0

docker exec -it [CONTAINER] bash
ip a
traceroute docker.com

iptables -t nat -L -n

docker history httdp | grep EXPOSE
```

Resource Manager

```
systemd-cgtop
```

Tool: **Cockpit** [^2]

## 3. Manage Compose

```
# list containers
docker-compose ps

# restart running containers
docker-compose restart [SERVICE...]
docker-compose restart database
```

## 4. Docker in Continuous Integration

**Using Docker in CI**

CI server builds Docker image and pushes into Docker Hub

**Docker Hub Auto Build**

* Docker Hub detects commits to source repository and builds the image
* Container is run during image build
* Testing done inside container

[^1]: [stackoverflow, Correct way to detach from a container without stopping it](http://stackoverflow.com/questions/25267372/correct-way-to-detach-from-a-container-without-stopping-it)
[^2]: [Docker management simplified – How to use Cockpit to deploy and manage Docker containers](https://bobcares.com/blog/docker-management-simplified-how-to-use-cockpit-to-deploy-and-manage-docker-containers/)
[^3]: [https://www.youtube.com/watch?v=3uvqEC8fWV0](Docker Tutorial 5 - Basic Networking)
