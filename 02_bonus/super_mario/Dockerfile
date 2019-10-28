FROM ubuntu:18.04

RUN apt-get update && \
	apt-get upgrade && \
	apt-get install sudo -y \
		git \
		build-essential \
		cmake \
		automake \
		libboost-all-dev \
		libcurl4-openssl-dev \
		libfreetype6-dev \
		libfribidi-dev \
		libglew-dev \
		libopenal-dev \
		libogg-dev \
		libphysfs-dev \
		libpng-dev \
		libraqm-dev \
		libsdl2-dev \
		libsdl2-image-dev \
		libvorbis-dev

WORKDIR /opt

RUN git clone --depth 1 --recurse-submodules https://github.com/SuperTux/supertux.git && \
	cd supertux && \
	git submodule update --init --recursive && \
	mkdir build && \
	cd build && \
	cmake .. && \
	make && \
	make install

ENTRYPOINT ["/opt/supertux/build/supertux2"]
