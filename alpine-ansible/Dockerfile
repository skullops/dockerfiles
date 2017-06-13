FROM wizdevops/python:2.7-alpine
LABEL MAINTAINER="Daniel Andrei Minca <mandrei17@gmail.com>"

RUN set -x \
  && apk add --update --no-cache \
    libffi-dev \
    openssl-dev \
    git \
    bash \
  && pip install \
    six \
    nose \
    httplib2

CMD ["bash"]

