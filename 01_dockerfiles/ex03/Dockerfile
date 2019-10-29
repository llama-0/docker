FROM ubuntu:18.04

ARG URL="0.0.0.0"

RUN apt-get update -y && \
	apt-get upgrade -y && \
	apt-get install sudo -y \
		curl \
		tzdata \
		openssh-server \
		ca-certificates \
		postfix && \
		curl -s https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | sudo bash

ENV EXT_URL $URL

RUN	sudo apt-get install -y gitlab-ce && \
	sudo echo "external_url \"http://${EXT_URL}\"" >> /etc/gitlab/gitlab.rb && \
	sudo mkdir -p /etc/gitlab/ssl && \
	sudo chmod 700 /etc/gitlab/ssl

COPY koparker.com.crt /etc/gitlab/ssl/koparker.com.crt

COPY koparker.com.key /etc/gitlab/ssl/koparker.com.key

RUN	apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

EXPOSE 80 443 22

ENTRYPOINT (/opt/gitlab/embedded/bin/runsvdir-start &) && \
	sudo gitlab-ctl reconfigure && \
	tail -f /dev/null

# to build an image:

# export URL=$(docker-machine ip Char); docker build --build-arg URL -t gitlab .

# to run the container:

# docker run --rm -it -p 2222:22 -p 443:443 -p 80:80 --privileged gitlab
