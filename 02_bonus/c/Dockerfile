FROM alpine

RUN apk update && \
	apk upgrade && \
	apk add \
		build-base \
		vim

WORKDIR /home/projects

# build and run:
# docker build -t c . && docker run --rm -it c
