FROM jenkins:alpine

USER root
RUN set -x \
  && apk add --update --no-cache \
    docker \
  && adduser jenkins docker
USER jenkins
