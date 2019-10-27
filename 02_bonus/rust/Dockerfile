FROM ubuntu:18.04

RUN apt-get update && \
	apt-get upgrade -y && \
	apt-get install sudo -y \
		curl \
		vim \
		build-essential

RUN curl https://sh.rustup.rs -sSf | bash -s -- -y

ENV PATH="/root/.cargo/bin:${PATH}"

WORKDIR /home/projects
