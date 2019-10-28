FROM ubuntu:18.04

RUN apt-get update -y && \
	apt-get upgrade -y && \
	apt-get install sudo -y \
		curl \
		tzdata \
		openssh-server \
		ca-certificates \
		postfix && \
		curl -s https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | sudo bash

EXPOSE 80 443 22

RUN	sudo apt-get install -y gitlab-ce && \
	apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

ENTRYPOINT (/opt/gitlab/embedded/bin/runsvdir-start &) && \
	sudo gitlab-ctl reconfigure && \
	tail -f /dev/null
