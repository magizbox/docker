# Docker Chrome

**Environment**

* Ubuntu 14.04
* Docker Engine 1.11

note: I can't make it run on CentOS.

### Dockerfile [^1]

[code]
# Base docker image
FROM debian:sid
MAINTAINER Jessica Frazelle <jess@docker.com>

ADD https://dl.google.com/linux/direct/google-talkplugin_current_amd64.deb /src/google-talkplugin_current_amd64.deb

# Install Chrome
RUN echo 'deb http://httpredir.debian.org/debian testing main' >> /etc/apt/sources.list && \
	apt-get update && apt-get install -y \
	ca-certificates \
	curl \
	hicolor-icon-theme \
	libgl1-mesa-dri \
	libgl1-mesa-glx \
	libv4l-0 \
	-t testing \
	fonts-symbola \
	--no-install-recommends \
	&& curl -sSL https://dl.google.com/linux/linux_signing_key.pub | apt-key add - \
	&& echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" > /etc/apt/sources.list.d/google.list \
	&& apt-get update && apt-get install -y \
	google-chrome-stable \
	--no-install-recommends \
	&& dpkg -i '/src/google-talkplugin_current_amd64.deb' \
	&& apt-get purge --auto-remove -y curl \
	&& rm -rf /var/lib/apt/lists/* \
	&& rm -rf /src/*.deb

COPY local.conf /etc/fonts/local.conf

RUN rm /etc/apt/sources.list.d/google-chrome.list

RUN apt-get update
RUN apt-get install -y libcanberra-gtk-module
RUN apt-get install -y dbus libdbus-1-dev libxml2-dev dbus-x11

# Autorun chrome
ENTRYPOINT [ "google-chrome" ]
CMD [ "--user-data-dir=/data" ]
[/code]

### Build Image

[code]
docker build -t chrome .
[/code]

### Docker Run

[code]
xhost +
docker run -it --net host --cpuset-cpus 0 -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY=unix$DISPLAY -v $HOME/chrome/data/Downloads:/root/Downloads -v $HOME/chrome/data/:/data -v /deb/shm:/dev/shm --device /dev/snd chrome --user-data-dir=/data www.google.com
[/code]

### Known Issue

Issue 1: Failed to load module "canberra-gtk-module" [^2]

[code]
Gtk-Message: Failed to load module "canberra-gtk-module"
[/code]

Issue 2: Chrome crash [^3]

Solution: add `-v /dev/shm:/dev/shm`

[^1]: [https://hub.docker.com/r/jess/chrome/~/dockerfile/](https://hub.docker.com/r/jess/chrome/~/dockerfile/)
[^2]: [http://fabiorehm.com/blog/2014/09/11/running-gui-apps-with-docker/#comment-2515573749](http://fabiorehm.com/blog/2014/09/11/running-gui-apps-with-docker/#comment-2515573749)
[^3]: [github, UnknownError: session deleted because of page crash from tab crashed](https://github.com/elgalu/docker-selenium/issues/20)