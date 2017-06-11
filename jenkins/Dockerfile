FROM jenkins:alpine

USER root
RUN set -x \
  && apk add --update --no-cache \
    docker \
    ansible \
    python2 \
    py-setuptools \
  && python2 -m ensurepip \
  && pip install docker-py
USER jenkins
