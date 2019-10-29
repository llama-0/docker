FROM debian

RUN apt-get update && apt-get upgrade -y && apt-get install -y \
	wget \
	lbzip2

RUN mkdir /koparker && \
	wget https://files.teamspeak-services.com/releases/server/3.9.1/teamspeak3-server_linux_amd64-3.9.1.tar.bz2 && \
	tar xvf teamspeak3-server_linux_amd64-3.9.1.tar.bz2 -C /koparker

RUN	mv /koparker/teamspeak3-server_* /koparker/teamspeak && \
	rm teamspeak3-server_linux_amd64-3.9.1.tar.bz2
	
#license
RUN echo "license_accepted=1" > /koparker/teamspeak/.ts3server_license_accepted

EXPOSE 9987/udp 10011 30033

ENTRYPOINT ["/koparker/teamspeak/ts3server_minimal_runscript.sh"]

# build:	docker build --tag teamspeak .
# run:		docker run --rm -it -p 9987:9987/upd -p 10011:10011 -p 30033:30033 teamspeak bash

# open teamspeak client on your host machine to test connection
