## Dockerfile

> Build a song with Dockerfile

A dockerfile is a configuration file that contains instructions for building a Docker image.

* Provides a more effective way to build images compared to using docker commit
* Easily fits into your continuous integration and deployment process.

**Command Line**

```
# `FROM` instruction specifies what the base image should be
FROM java:7

# `RUN` instruction specifies a command to execute
RUN apt-get update && apt-get install -y \
      curl \
      vim \
      openjdk-7-jdk

# CMD
# Defines a default command to execute when a container is created
CMD ["ping", "127.0.0.1", "-c", "30"]

# ENTRYPOINT
# Defines the command that will run when a container is executed
ENTRYPOINT ["ping"]
```

**Volumes**

> Configuration Files and Directories**

```
COPY <src>... <dest>
COPY hom* /mydir/        # adds all files starting with "hom"
COPY hom?.txt /mydir/    # ? is replaced with any single character, e.g., "home.txt"
```

**Networking**

* Ports still need to be mapped when container is executed

```
# EXPOSE
# Configures which ports a container will listen on at runtime
FROM ubuntu:14.04
RUN apt-get update
RUN apt-get install -y nginx

EXPOSE 80 443

CMD ["nginx", "-g", "daemon off;"]
```

### 2.4 Linking Containers

> Example: Web app container and Database container

Linking is a communication method between containers which allows them to securely transfer data from one to another

* Source and recipient containers
* Recipient containers have access to data on source containers
* Links are established based on container names

**Create a Link**

1. Create the source container first
2. Create the recipient container and use the `--link` option

* **Best practice** - give your containers meaningful names

```
Create the source container using the postgres
docker run -d --name database postgres

Create the recipient container and link it
docker run -d -P --name website --link database:db nginx
```

**Uses of Linking**

* Containers can talk to each other without having to expose ports to the host
* Essential for micro service application architecture
* Example:
    * Container with the Tomcat running
    * Container with the MySQL running
    * Application on Tomcat needs to connect to MySQL

### Operating Systems for Docker [^1] [^2]

<table>
<tr>
<th>Operating System</td>
<th>Features</td>
</tr>
<tr>
<td>CoreOS</td>
<td>Service Discovery, Cluster management, Auto-updates<br/>
CoreOS is designed for security, consistency, and reliability. Instead of installing packages via yum or apt, CoreOS uses Linux containers to manage your services at a higher level of abstraction. A single service’s code and all dependencies are packaged within a container that can be run on one or many CoreOS machines</td>
</tr>
</table>

[^1]: [The New Minimalist Operating Systems](https://blog.docker.com/2015/02/the-new-minimalist-operating-systems/)
[^2]: [Top 5 operating systems for your Docker infrastructure](https://bobcares.com/blog/top-5-operating-systems-for-your-docker-infrastructure/)
