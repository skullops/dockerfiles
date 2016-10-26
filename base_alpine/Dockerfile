FROM alpine:edge
MAINTAINER Minca Daniel Andrei <mandrei17@gmail.com>
ENV TERM dumb
RUN set -x \
		&& echo "http://dl-cdn.alpinelinux.org/alpine/edge/testing" > /etc/apk/repositories \
		&& echo "http://dl-cdn.alpinelinux.org/alpine/edge/community" >> /etc/apk/repositories \
		&& echo "http://dl-cdn.alpinelinux.org/alpine/edge/main" >> /etc/apk/repositories \
    && apk update && apk upgrade --no-cache \
    && rm -rf /var/cache/apk/*

