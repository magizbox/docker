## Docker-Compose [^1]

> Compose a symphony

Compose is a tool for defining and running multi-container Docker applications. With Compose, you use a Compose file to configure your application’s services. Then, using a single command, you create and start all the services from your configuration. To learn more about all the features of Compose see the list of features.
Docker Compose `Describes the components of an application`

Box your component

```
.component/
├── docker-compose.yml
├── app-1/
│   ├── app/
│   │   ├── file-1
│   │   └── file-2
│   ├── Dockerfile
│   └── run.sh
└── app-2/
    ├── app/
    │   ├── file-1
    │   └── file-2
    ├── Dockerfile
    └── run.sh
```

**Services**

**Networks**

`network_mode`, `ports`, `external_hosts`, `link`, <del datetime="2016-04-06T15:21:55+00:00">`net`</del>

```
network_mode: "bridge"
network_mode: "host"
network_mode: "service:[service_name]"
network_mode: "container:[container name/id]"
```

**Volumes**

**Usage**

```
# rebuild your images
docker-compose build

# build or rebuild services
docker-compose build [SERVICE...]
docker-compose build --no-cache database


# start all the containers
docker-compose up -d
docker-compose up

# stops the containers
docker-compose stop [CONTAINER]
```

Keep a container running in compose [^2]

You can use one of those lines

```
command: "top"
command: "tail -f /dev/null"
command: "sleep infinity"
```

[^1]: [Docker Compose Files Version 2](https://www.youtube.com/watch?v=EReEOMS7gsk)
[^2]: [github issue, Keep a container running in compose](https://github.com/docker/compose/issues/1926)