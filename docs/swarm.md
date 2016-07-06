# Docker Swarm

Docker Swarm is native clustering for Docker. It turns a pool of Docker hosts into a single, virtual Docker host. Because Docker Swarm serves the standard Docker API, any tool that already communicates with a Docker daemon can use Swarm to transparently scale to multiple hosts [^1]

### Architecture [^2]

![](http://blog.arungupta.me/wp-content/uploads/2015/04/docker-swarm-cluster.png)

**Swarm Manager**: Docker Swarm has a Master or Manager, that is a pre-defined Docker Host, and is a single point for all administration. Currently only a single instance of manager is allowed in the cluster. This is a SPOF for high availability architectures and additional managers will be allowed in a future version of Swarm with #598.

**Swarm Nodes**: The containers are deployed on Nodes that are additional Docker Hosts. Each Swarm Node  must be accessible by the manager, each node must listen to the same network interface (TCP port). Each node runs a node agent that registers the referenced Docker daemon, monitors it, and updates the discovery backend with the node’s status. The containers run on a node.

**Scheduler Strategy**: Different scheduler strategies (binpack, spread, and random) can be applied to pick the best node to run your container. The default strategy is spread which optimizes the node for least number of running containers. There are multiple kinds of filters, such as constraints and affinity.  This should allow for a decent scheduling algorithm.

**Node Discovery Service**: By default, Swarm uses hosted discovery service, based on Docker Hub, using tokens to discover nodes that are part of a cluster. However etcd, consul, and zookeeper can be also be used for service discovery as well. This is particularly useful if there is no access to Internet, or you are running the setup in a closed network. A new discovery backend can be created as explained here. It would be useful to have the hosted Discovery Service inside the firewall and #660 will discuss this.

**Standard Docker API**: Docker Swarm serves the standard Docker API and thus any tool that talks to a single Docker host will seamlessly scale to multiple hosts now. That means if you were using shell scripts using Docker CLI to configure multiple Docker hosts, the same CLI would can now talk to Swarm cluster and Docker Swarm will then act as proxy and run it on the cluster.

### Create Swarm

* [Simple Swarm](http://magizbox.com/index.php/tools/docker/docker-swarm/docker-swarm-simple-swarm/)
* [Swarm with CentOS](http://magizbox.com/index.php/tools/docker/docker-swarm/docker-swarm-centos/)
* [Swarm with Windows](http://magizbox.com/index.php/tools/docker/docker-swarm/docker-swarm-windows/)

### Swarm and Compose [^8]

Create `docker-compose.yml` file

Example

```
wget https://docs.docker.com/swarm/swarm_at_scale/docker-compose.yml
```

### Discovery [^6]

![](http://blog.arungupta.me/wp-content/uploads/2015/12/docker-swarm-machine-compose-1024x763.png)

### Scheduling [^5]


[^1]: [Docker Swarm overview](https://docs.docker.com/swarm/overview/)
[^2]: [Docker Tutorial 11 - Docker Swarm](https://www.youtube.com/watch?v=zTKGfPfhg78)
[^5]: [Docker Swarm Part 3: Scheduling](https://www.youtube.com/watch?v=7B_bX3czq-Y)
[^6]: [Docker Swarm Part 2: Discovery](https://www.youtube.com/watch?v=4t7nej89dk4)
[^8]: [Deploy the application](https://docs.docker.com/swarm/swarm_at_scale/deploy-app/)

# Docker Swarm: CentOS

## Prerequisites

* Docker 1.10.3
* CentOS 7

## Create cluster [^1]

Receipts: `consult`

**Configure daemon** in each host [^3]

Edit `/etc/systemd/system/docker.service.d/docker.conf`

```
[Service]
ExecStart=
ExecStart=/usr/bin/docker daemon -H fd:// -D -H tcp://<node_ip>:2375 --cluster-store=consul://<consul_ip>:8500 --cluster-advertise=<node_ip>:2375
```

Restart docker

```
systemctl daemon-reload
systemctl restart docker
```

Verify docker run with config

```
ps aux | grep docker | grep -v grep
```

**Run cluster**

In `discovery host`

```
# run consul
docker run -d -p 8500:8500 --name=consul progrium/consul -server -bootstrap
```

In `swarm manage host`

```
# run swarm master
docker run -d -p 2376:2375 swarm manage consul://<consul_ip>:8500/swarm
```

In `swarm node host`

```
# open 2375 port
firewalld-cmd --get-active-zones
firewall-cmd --zone=public --add-port=2375/tcp --permanent
firewall-cmd --reload

# run swarm node
docker run -d swarm join --addr=<node_ip>:2375 consul://<consul_ip>:8500/swarm
```

> Question: Why manager and consul cannot run in the same host? (because docker-proxy?)

**Verify** [^2]

```
# manage
docker -H :2376 info
export DOCKER_HOST=tcp://<ip>:12375
docker info
docker run -d -P redis

# debug a swarm
docker swarm --debug manage consul://<consul_ip>:8500
```

[^1]: [Build a Swarm cluster for production](https://docs.docker.com/swarm/install-manual/)
[^2]: [Docker-swarm, Cannot connect to the docker engine endpoint](http://stackoverflow.com/questions/34810779/docker-swarm-cannot-connect-to-the-docker-engine-endpoint)
[^3]: [Configuring and running Docker on various distributions](https://docs.docker.com/engine/admin/configuring/)

# Docker Swarm: Simple Swarm

### Simple Swarm in one node with `token` [^1]

Change file `vi /etc/default/docker`

DOCKER_OPTS="-H tcp://0.0.0.0:2375 -H unix:///var/run/docker.sock"

```
# Restart docker
service docker restart

# create swarm token
docker run --rm swarm create
> token_id

# Run swarm node
docker run -d swarm join --addr=ip:2375 token://token_id
docker ps

# Run swarm manager
docker run -d -p 12375:2375 swarm manage token://token_id

# Swarm info
docker -H :12375 info

export DOCKER_HOST=tcp://ip:12375
docker info
docker run -d -P redis
```

[^1]: [Giới thiệu và chạy thử Docker Swarm](https://www.youtube.com/watch?v=sYW0mmWbLyY)

## Docker Swarm: Windows

## Prerequisites

* Docker 1.10.3