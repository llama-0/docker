FROM ubuntu:18.04

RUN apt-get update -y && \
	apt-get upgrade -y && \
	apt-get install sudo -y \
		curl \
		openssh-server \
		ca-certificates \
		postfix && \
		curl -s https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | sudo bash

EXPOSE 80 443 22

RUN	sudo apt-get install -y gitlab-ce && \
	sudo echo 'external_url "https://koparker.com"' >> /etc/gitlab/gitlab.rb && \
	sudo echo 'nginx['redirect_http_to_https'] = true' >> /etc/gitlab/gitlab.rb && \
	sudo echo 'nginx['ssl_certificate'] = "/etc/gitlab/ssl/koparker.com.crt"' >> /etc/gitlab/gitlab.rb && \
	sudo echo 'nginx['ssl_certificate_key'] = "/etc/gitlab/ssl/koparker.com.key"' >> /etc/gitlab/gitlab.rb && \
	sudo mkdir -p /etc/gitlab/ssl && \
	sudo chmod 700 /etc/gitlab/ssl

COPY koparker.com.crt /etc/gitlab/ssl/koparker.com.crt

COPY koparker.com.key /etc/gitlab/ssl/koparker.com.key

ENTRYPOINT cat -n /etc/gitlab/gitlab.rb && \
	service ssh start && \
	(/opt/gitlab/embedded/bin/runsvdir-start &) && \
	sudo gitlab-ctl reconfigure && \
	tail -f /dev/null
