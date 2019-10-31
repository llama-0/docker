FROM ubuntu:18.04

RUN apt-get update && \
	apt-get upgrade -y && \
	apt-get install sudo -y \
		telnet

ENTRYPOINT telnet towel.blinkenlights.nl

# sh setup
