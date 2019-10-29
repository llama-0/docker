FROM ubuntu:18.04

RUN apt-get update && \
	apt-get upgrade && \
	apt-get install sudo -y \
		build-essential \
		git \
		libncurses5-dev

WORKDIR /home/projects

RUN git clone https://github.com/alexdantas/nSnake.git && \
	cd nSnake && \
	make && \
	make install
	
# sh setup
