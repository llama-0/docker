FROM ubuntu:18.04

RUN apt-get update && \
	apt-get upgrade -y && \
	apt-get install sudo -y \
		build-essential \
		git \
		libncurses5-dev

WORKDIR /home/projects

RUN git clone https://github.com/llama-0/yetris.git && \
	cd yetris && \
	make && \
	make install
	
# sh setup
