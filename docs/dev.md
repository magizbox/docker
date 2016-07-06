# Dev

### Create New Image

```
# Create new image by commit
docker commit <container ID> <yourname>/curl:1.0

# Build image
docker build -t ubuntu/test:1.0 .
docker build -t ubuntu/test:1.0 --no-cache .
```

### Import/Export Container [^3] [^4]

Export the contents of a container's filesystem as a tar archive

```
docker export [OPTIONS] CONTAINER
docker export red_panda > latest.tar

docker import file|URL|- [REPOSITORY[:TAG]]
docker import http://example.com/exampleimage.tgz
cat exampleimage.tgz | docker import - exampleimagelocal:new
```

### Save/Load Image [^5] [^6]

Save one or more images to a tar archive

```
docker save [OPTIONS] IMAGE [IMAGE...]
docker save busybox > busybox.tar.gz

docker load [OPTIONS]
docker load < busybox.tar.gz
```

### Push Images to Docker Hub

```
# Login to docker hub
docker login --username=yourhubusername --email=youremail@company.com

# push docker
docker push [repo:tag]

# tag an image into a repository
docker tag [OPTIONS] IMAGE[:TAG] [REGISTRYHOST/][USERNAME/]NAME[:TAG]
```

### Windows

[5 Useful Docker Tips and Tricks on Windows](http://blog.pavelsklenar.com/5-useful-docker-tip-and-tricks-on-windows/)


[^3]: [Commandline Reference: export](https://docs.docker.com/engine/reference/commandline/export/)
[^4]: [Commandline Reference: import](https://docs.docker.com/engine/reference/commandline/import/)
[^5]: [Commandline Reference: save](https://docs.docker.com/engine/reference/commandline/save/)
[^6]: [Commandline Reference: load](https://docs.docker.com/engine/reference/commandline/load/)