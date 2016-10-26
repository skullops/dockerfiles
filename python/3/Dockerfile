FROM dminca/alpine
MAINTAINER Minca Daniel Andrei <mandrei17@gmail.com>

RUN apk add --update --no-cache \
	python3 \
	musl \
	linux-headers \
	build-base \
	bash \
	git \
	ca-certificates \
	python \
	python-dev \
  && python3 -m ensurepip \
  && rm -r /usr/lib/python*/ensurepip \
  && pip3 install --upgrade pip setuptools virtualenv \
  && rm -r /root/.cache
