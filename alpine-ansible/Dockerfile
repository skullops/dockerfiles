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

ADD https://raw.githubusercontent.com/ansible/ansible/devel/requirements.txt /tmp

# install Ansible requirements
RUN set -x \
  && pip install --no-cache-dir -r /tmp/requirements.txt

CMD ["bash"]

