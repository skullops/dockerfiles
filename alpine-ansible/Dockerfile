FROM wizdevops/python:2.7-alpine
LABEL MAINTAINER="Daniel Andrei Minca <mandrei17@gmail.com>"

RUN set -x \
  && apk add --update --no-cache \
    libffi-dev \
    openssl-dev \
    git \
    bash \
  && git clone https://github.com/ansible/ansible.git --recursive \
  && pip install -r /ansible/requirements.txt \
  && pip install \
    six \
    nose \
    httplib2

CMD ["bash"]

