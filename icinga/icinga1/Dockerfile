FROM wizdevops/alpine
MAINTAINER Daniel Andrei Minca <telegram.me/dminca>
# Metadata params
ARG BUILD_DATE
ARG VERSION
ARG VCS_URL
ARG VCS_REF
LABEL org.label-schema.build-date=$BUILD_DATE \
      org.label-schema.vcs-url=$VCS_URL \
      org.label-schema.vcs-ref=$VCS_REF \
      org.label-schema.version=$VERSION \
      org.label-schema.name='Icinga1 Classic UI Alpine' \
      org.label-schema.description='Icinga1 Classic UI image on Alpine Linux' \
      org.label-schema.usage='https://github.com/WizDevOps/dockerfiles' \
      org.label-schema.url='https://github.com/WizDevOps/dockerfiles' \
      org.label-schema.vendor='Daniel Andrei Minca' \
      org.label-schema.schema-version='1.0' \
      org.label-schema.docker.cmd='docker run --rm wizdevops/icinga:1-alpine' \
      org.label-schema.docker.cmd.devel='docker run --rm -ti wizdevops/icinga:1-alpine ash' \
      org.label-schema.docker.debug='docker logs $CONTAINER' \
      io.github.dminca.docker.dockerfile="/Dockerfile" \
      io.github.dminca.license="GPLv3"
RUN set -x \
  && apk add --update --no-cache \

    # required to build from source
    # git \
    # alpine-sdk \
    # gd-dev \
    # libjpeg \
    # libpng \
    # libpng-dev \
    # perl \
    # perl-dev \

  # install SNMP packages
  net-snmp \
  net-snmp-dev \
  net-snmp-tools \
  net-snmp-libs \
  icinga2
