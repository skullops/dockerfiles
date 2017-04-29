FROM wizdevops/python:2.7-alpine
MAINTAINER Daniel Andrei Minca <mandrei17@gmail.com>

RUN set -x \
  && apk add --update --no-cache \
    libffi-dev \
    openssl-dev \
    git \
    bash \
  && git clone git://github.com/ansible/ansible.git --recursive \
  && source /ansible/hacking/env-setup \
  && pip install -r /ansible/requirements.txt \
  && bash -c "pushd /ansible; git pull --rebase; pushd"

CMD ansible --version
