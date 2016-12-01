FROM wizdevops/alpine
MAINTAINER Daniel Andrei Minca <telegram.me/dminca>
# Metadata params
ARG BUILD_DATE
ARG VERSION
ARG VCS_URL
ARG VCS_REF
ENV ICINGA_VERSION=1.13.3 \
  DB_TYPE=${DB_TYPE:-pgsql} \
  DB_HOST=${DB_HOST:-psql} \
  DB_NAME=${DB_NAME:-icinga_web} \
  DB_PORT=${DB_PORT:-icinga_web} \
  DB_USER=${DB_USER:-icinga_web} \
  DB_PASS=${DB_PASS:-icinga_web}
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
    git \
    alpine-sdk \
    gd-dev \
    libjpeg \
    libpng \
    libpng-dev \
    perl \
    perl-dev \

  # install SNMP packages
  net-snmp \
  net-snmp-dev \
  net-snmp-tools \
  net-snmp-libs \

  # user/group configs
  && adduser -h /home/icinga -D icinga \
  && addgroup icinga icinga \
  && adduser -D icinga-cmd \
  && addgroup www-data \
  && addgroup icinga-cmd icinga \
  && addgroup icinga-cmd www-data \

  # proceed building
  && mkdir -p /usr/src /var/log/icinga; cd /usr/src \
  && wget https://github.com/Icinga/icinga-core/releases/download/v"$ICINGA_VERSION"/icinga-"$ICINGA_VERSION".tar.gz \
  && cd icinga-"$ICINGA_VERSION"; tar xvf icinga-"$ICINGA_VERSION".tar.gz \
  && ./configure \
  --prefix=/usr/local/icinga-web \
  --with-web-user=www-data \
  --with-web-group=www-data \
  --with-web-path=/icinga-web \
  --with-web-apache-path=/etc/apache2/conf.d \
  --with-db-type=$DB_TYPE \
  --with-db-port=$DB_PORT \
  --with-db-host=$DB_HOST \
  --with-db-name=$DB_NAME \
  --with-db-user=$DB_USER \
  --with-db-pass=$DB_PASS \
  --with-conf-dir=etc/conf.d \
  --with-log-dir=/var/log/icinga \
  --with-api-host=$DB_HOST \
  --with-api-subtype=pgsql \
  --with-api-port=$DB_PORT \
