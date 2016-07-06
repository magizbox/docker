# Docker Labs

**Lab 1**:

```
# 1. Create a container from an Ubuntu image and run a bash terminal
docker run -it ubuntu /bin/bash
# 2.Inside the container install curl
apt-get install curl
# 3. Exit the container terminal
Ctrl-P
# 4. Run `docker ps -a` and take not of your container ID
# 5. Save the container as a new image. For the repository name use <yourname>/curl. Tag the image as 1.0
# 6. Run `docker images` and verify that you can see your new image
```


**Lab 2**: Run Ubntu

```
FROM ubuntu:14.04
RUN apt-get update && apt-get install -y curl \ vim
```

```
# 1. Go into the test folder and open your Dockerfile from the previous exercise

# 2. Add the folloing line to the end
CMD ["ping", "127.0.0.1", "-c", "30"]

# 3. Build the image
docker build -t <yourname>/testimage:1.1 .

# 4. Execute a container from the image and observe the output
docker run <yourname>/testimage:1.1

# 5. Execute another container from the image and specify the echo command
docker run <yourname>/testimage:1.1 echo "hello world"

# 6. Observe how the container argument overrides the CMD instruction
```

**Lab:**

```
1) In your home directory, create a folder called test
2) In the test folder, create a file called `Dockerfile`
3) In the file, specify to use Ubuntu 14.04 as the base image
FROM ubuntu:14.04
4) Write an instruction to install curl and vim after an apt-get update
RUN apt-get update && apt-get install -y curl \ vim
5) Build an image from Dockerfile. Give it the repository <yourname>/testimage and tag it as 1.0
docker build -t johnnytu/testimage:1.0 .
6) Create a container using your newly build image and verify that curl and vim are installed.
```


**Lab:** Run a container and get Terminal Access

```
* Create a container using the ubuntu image and connect to STDIN and a terminal
docker run -i -t ubuntu /bin/bash
* In your container, create a new user using your first and last name as the
username
addusername username
* Exit the container
exit
* Notice how the container shutdown
* Once again run:
docker run -i -t ubuntu /bin/bash
* Try and find your user `cat /etc/passwd`
* Noice that it does not exist.
```

**Lab:** Run a web application inside a container

```
# The -P flag to map container ports to host ports
docker run -d -P tomcat:7
docker ps     # check your image details runing
go to <server url>:<port number> # verify that you can see the Tomcat page
```

**Lab** Create a Docker Hub Account

**Lab** Push Images to Docker Hub

```
# Login to docker hub
$ docker login --username=yourhubusername --email=youremail@company.com
Password:
WARNING: login credentials saved in C:\Users\sven\.docker\config.json
Login Succeeded

# Use `docker push` command
docker push [repo:tag]

# Local repo must have same name and tag as the Docker Hub repo

# Used  to rename a local image repository before pushing to Docker Hub
docker tag [image ID] [repo:tag]
docker tag [local repo:tag] [Docker Hub repo:tag]

> tag image with ID (trainingteam/testexample is the name of repository on Docker hub)
docker tag edfc212de17b trainingteam/testexample:1.0

> tag image using the local repository tag
docker tag johnnytu/testimage:1.5 trainingteam/testexample
```