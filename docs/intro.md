[embed]https://www.youtube.com/watch?v=cRczhEvSH2A[/embed]

## Docker Promise [^6] [^7]

> Docker provides an integrated technology suite that enables development and IT operations teams to build, ship, and run distributed applications anywhere.

![](https://www.docker.com/sites/default/files/enterprise/docker_diagram51.svg)

**Build**: Docker allows you to compose your application from microservices, without worrying about inconsistencies between development and production environments, and without locking into any platform or language.

`Composable` You want to be able to split up your application into multiple services.

**Ship**: Docker lets you design the entire cycle of application development, testing and distribution, and manage it with a consistent user interface.

`Portable across providers` You want to be able to move your application between different cloud providers and your own servers, or run it across several providers.

**Run**: Docker offers you the ability to deploy scalable services, securely and reliably, on a wide variety of platforms.

`Portable across environments` You want to be able to define how your application will run in development, and then run it seamlessly in testing, staging and production.

## 1. Docker Architecture [^3]

![](https://docs.docker.com/v1.8/article-img/architecture.svg)

**Docker Containers vs Virtual Hypervisor Model** [^1]

<img src="http://www.eweek.com/imagesvr_ce/8781/DockerFacts_3.jpg" alt="" />

In the Docker container model, the Docker engine sits atop a single host operating system. In contrast, with the traditional virtualization hypervisor mode, a separate guest operating system is required for each virtual machine.

**Docker Images and Docker Containers**

<img src="http://devopscube.com/wp-content/uploads/2015/02/docker-filesystems-busyboxrw.png" alt="" />

## 2.1 Docker Images [^2]

> Docker images are the **build component** of Docker.

*For example, an image could contain an Ubuntu operating system with Apache and your web application installed. Images are used to create Docker containers.*

Docker provides a simple way to build new images or update existing images, or you can download Docker images that other people have already created.

Built by you or other Docker users

Stored in the Docker Hub or your local Registry

**Images Tags**

* Images are specified by repository:tag
* The same image my have multiple tags
* The default tag is `lastest`
* Look up the repository on Docker to see what tags are available

## 2.2 Docker Containers [^3]

> Docker containers are the **run component** of Docker.

Docker containers are similar to a directory. A Docker container holds everything that is needed for an application to run. Each container is created from a Docker image. Docker containers can be run, started, stopped, moved, and deleted. Each container is an isolated and secure application platform.

### 2.3 Registry and Repository

> Docker registries are the **distribution component** of Docker.

Docker registries

Docker registries hold images. These are public or private stores from which you upload or download images. The public Docker registry is provided with the Docker Hub. It serves a huge collection of existing images for your use. These can be images you create yourself or you can use images that others have previously created.
Docker Hub

Docker Hub is the public registry that contains a large number of images available for your use.

### 2.3 Docker Networking [^5]

1. Docker use DNS instead `etc/hosts`

## 3. Docker Orchestration [^2]

* Three tools for orchestrating distributed applications with Docker
* Docker Machine
    * Tool that provisions Docker hosts and installs the Docker Engine on them
* Docker Swarm
    * Tool that clusters many Engines and schedules containers
* Docker Compose
    * Tool to create and manage multi-container applications

## Installation

Docker only supports <code>CentOS 7,  Windows 7.1, 8/8.1, Mac OSX 10.8</code> <code>64bit</code>

[Windows](http://magizbox.com/index.php/tools/docker/docker-why-and-what/docker-windows/), [CentOS](http://magizbox.com/index.php/tools/docker/docker-why-and-what/docker-centos-7/)

## Usage

#### Lab: Search for Images on Docker Hub

[^1]: <a href="http://www.eweek.com/cloud/slideshows/10-quick-facts-about-docker-container-virtualization.html">10 Quick Facts About Docker Container Virtualization</a>
[^2]: [Self Paced Training, Docker Fundamentals](https://training.docker.com/self-paced-training)
[^3]: [Understand the architecture](https://docs.docker.com/v1.8/introduction/understanding-docker/)
[^4]: <a href="https://docs.docker.com/introduction/understanding-docker/">Understand the architecture</a>
[^5]: [Docker Compose and Networking](https://www.youtube.com/watch?v=rFQqiuFIjms)
[^6]: [https://www.docker.com/](https://www.docker.com/)
[^7]: [Orchestrating Docker with Machine, Swarm and Compose](https://blog.docker.com/2015/02/orchestrating-docker-with-machine-swarm-and-compose/)

## Installation: Ubuntu

## Installation [^1]

`ubuntu 14.04`

**Prerequisites**

```
apt-get update
apt-get install apt-transport-https ca-certificates

apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D
```

Edit `/etc/apt/sources.list.d/docker.list`

```
deb https://apt.dockerproject.org/repo ubuntu-trusty main
```

```
apt-get update
apt-get purge lxc-docker
apt-cache policy docker-engine
```

**Install docker**

```
apt-get update
apt-get install -y --force-yes docker-engine
service docker start
```


**Run Docker**

```
docker run hello-world
docker info
docker version
```

[^1]: [Docker document](https://docs.docker.com/engine/installation/linux/ubuntulinux/)

### Installation [^1]

https://www.docker.com/products/docker-toolbox

1. Go to the [Docker Toolbox](https://www.docker.com/docker-toolbox) page.
2. Click the installer link to download.
3. Install Docker Toolbox by double-clicking the installer.

## Docker: CentOS 7

### Installation [^1]

Install Docker

```
# make sure your existing yum packages are up-to-date.
sudo yum -y update

# add docker repo
sudo tee /etc/yum.repos.d/docker.repo <<-'EOF'
[dockerrepo]
name=Docker Repository
baseurl=https://yum.dockerproject.org/repo/main/centos/$releasever/
enabled=1
gpgcheck=1
gpgkey=https://yum.dockerproject.org/gpg
EOF

# install the Docker package.
sudo yum install -y docker-engine

# start the Docker daemon
sudo service docker start

# verify
sudo docker run hello-world
```

Install Docker Compose

```
sudo yum install epel-release
sudo yum install -y python-pip

sudo pip install docker-compose
```

[^1]: [Installation docker in CentOS](https://docs.docker.com/engine/installation/linux/centos/)




[Docker 1.10.3](https://github.com/docker/toolbox/releases/download/v1.10.3/DockerToolbox-1.10.3.exe)

[^1]: [Install Docker for Windows](https://docs.docker.com/windows/step_one/)

### Kitematic

#### Port Forwarding

Open Virtualbox


#### Volumes