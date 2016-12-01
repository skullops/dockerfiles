FROM wizdevops/alpine
MAINTAINER Daniel Andrei Minca <mandrei17@gmail.com>
# Metadata params
ARG BUILD_DATE
ARG VERSION
ARG VCS_URL
ARG VCS_REF
# Metadata
LABEL org.label-schema.build-date=$BUILD_DATE \
      org.label-schema.vcs-url=$VCS_URL \
      org.label-schema.vcs-ref=$VCS_REF \
      org.label-schema.version=$VERSION \
      org.label-schema.name="Nginx with PHP 7" \
      org.label-schema.description="Nginx with PHP 7 image running on Alpine \
Linux, super slim, fast and easy." \
      org.label-schema.usage='https://github.com/WizDevOps/dockerfiles' \
      org.label-schema.url='https://github.com/WizDevOps/dockerfiles' \
      org.label-schema.vendor='Daniel Andrei Minca' \
      org.label-schema.schema-version='1.0' \
      org.label-schema.docker.cmd='docker run --rm wizdevops/nginx:alpine' \
      org.label-schema.docker.cmd.devel='docker run --rm -ti wizdevops/nginx:alpine ash' \
      org.label-schema.docker.debug='docker logs $CONTAINER' \
      io.github.dminca.docker.dockerfile="/Dockerfile" \
      io.github.dminca.license="GPLv3"
RUN set -x \
  && apk add --update --no-cache \
  nginx \
  php7 \
  php7-pear \
  php7-xmlrpc \
  php7-xsl \
  php7-soap \
  php7-gd \
  php7-ldap \
  php7-pgsql \
  php7-fpm \
  fcgiwrap \
  && ln -s /usr/bin/php7 /usr/bin/php
