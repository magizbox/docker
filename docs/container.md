### Container

#### Lifecycle

* `docker create` creates a container but does not start it.
* `docker rename` allows the container to be renamed.
* `docker run` creates and starts a container in one operation.
* `docker rm` deletes a container.
* `docker update` updates a container's resource limits.

#### Starting and Stopping

* `docker start` starts a container so it is running.
* `docker stop` stops a running container.
* `docker restart` stops and starts a container.
* `docker pause` pauses a running container, "freezing" it in place.
* `docker unpause` will unpause a running container.
* `docker wait` blocks until running container stops.
* `docker kill` sends a SIGKILL to a running container.
* `docker attach` will connect to a running container.

#### Info

* `docker ps` shows running containers.
* `docker logs` gets logs from container. (You can use a custom log driver, but logs is only available for json-file and * journald in 1.10).
* `docker inspect` looks at all the info on a container (including IP address).
* `docker events` gets events from container.
* `docker port` shows public facing port of container.
* `docker top` shows running processes in container.
* `docker stats` shows containers' resource usage statistics.
* `docker diff` shows changed files in the container's FS.

#### Import / Export

* `docker cp` copies files or folders between a container and the local filesystem.
* `docker export` turns container filesystem into tarball archive stream to STDOUT.

Example

```
docker cp foo.txt mycontainer:/foo.txt
docker cp mycontainer:/foo.txt foo.txt
```

Note that docker cp is not new in `Docker 1.8`. In older versions of Docker, the docker cp command only allowed copying files from a container to the host

#### Executing Commands

* `docker exec` to execute a command in container.

To enter a running container, attach a new shell process to a running container called foo

```
docker exec -it foo /bin/bash.
```

**Suggest Readings**: [docker cheatsheet](https://github.com/wsargent/docker-cheat-sheet#containers)