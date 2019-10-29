FROM alpine

RUN apk update && apk upgrade && apk add vim

ENTRYPOINT vim

# build an image: docker build --tag vim_container .
# run the container: docker run --rm -it vim_container
