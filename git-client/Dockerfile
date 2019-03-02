FROM alpine:latest

LABEL maintainer="Rizon"

LABEL description="same as apline/git,remove ENTRYPOINT"

RUN apk --update add git less openssh && \
    rm -rf /var/lib/apt/lists/* && \
    rm /var/cache/apk/*

VOLUME [/git]

WORKDIR /git