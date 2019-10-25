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
