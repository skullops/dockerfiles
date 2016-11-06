FROM wizdevops/alpine
# Metadata params
ARG BUILD_DATE
ARG VERSION
ARG VCS_URL
ARG VCS_REF
LABEL org.label-schema.build-date=$BUILD_DATE \
      org.label-schema.vcs-url=$VCS_URL \
      org.label-schema.vcs-ref=$VCS_REF \
      org.label-schema.version=$VERSION \
      org.label-schema.name='Python 2.7 Alpine Linux' \
      org.label-schema.description='Python 2.7 on base Alpine Linux image to make it slim as fuck' \
      org.label-schema.usage='https://github.com/WizDevOps/dockerfiles' \
      org.label-schema.url='https://github.com/WizDevOps/dockerfiles' \
      org.label-schema.vendor='Daniel Andrei Minca' \
      org.label-schema.schema-version='1.0' \
      org.label-schema.docker.cmd='docker run --rm wizdevops/python:2.7-alpine' \
      org.label-schema.docker.cmd.devel='docker run --rm -ti wizdevops/python:2.7-alpine ash' \
      org.label-schema.docker.debug='docker logs $CONTAINER' \
      io.github.dminca.docker.dockerfile="/Dockerfile" \
      io.github.dminca.license="GPLv3"
RUN set -x \
      && apk add --update --no-cache \
      musl \
      linux-headers \
      build-base \
      ca-certificates \
      python2 \
      python2-dev \
      py-setuptools \
      && python2 -m ensurepip \
      && rm -rv /usr/lib/python*/ensurepip \
      && pip install --upgrade pip setuptools virtualenv \
      && rm -rv /root/.cache
