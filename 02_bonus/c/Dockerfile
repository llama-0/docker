FROM alpine

RUN apk update && \
	apk upgrade -y && \
	apk add -y \
		build-base \
		vim

WORKDIR /home/projects

# build and run:
# docker build -t c . && docker run --rm -it c
