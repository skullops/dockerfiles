FROM wizdevops/alpine
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
      org.label-schema.name="Drupal 8 volume on Alpine Linux" \
      org.label-schema.description="Drupal 8 files and folders volume on Alpine Linux" \
      org.label-schema.usage='https://github.com/WizDevOps/dockerfiles' \
      org.label-schema.url='https://github.com/WizDevOps/dockerfiles' \
      org.label-schema.vendor='Daniel Andrei Minca' \
      org.label-schema.schema-version='1.0' \
      org.label-schema.docker.cmd='docker run --rm wizdevops/drupal:8-volume' \
      org.label-schema.docker.cmd.devel='docker run --rm -ti wizdevops/drupal:8-volume ash' \
      org.label-schema.docker.debug='docker logs $CONTAINER' \
      io.github.dminca.docker.dockerfile="drupal/drupal-volume/Dockerfile" \
      io.github.dminca.license="GPLv3" \
      MAINTAINER="Minca Daniel Andrei <dminca@protonmail.com>"
ENV DRUPAL_VERSION='drupal-8.4.4' \
  DRUPAL_SHA='d2441f8e42f3dcb26f8ef00c8e07ee25c57f5437b0d9ac56119a4aa3930e7a5b'
RUN set -x \
    && apk add --update --no-cache \
      tar \
      curl \
    && mkdir -vp /var/www/html \
    && cd /var/www/html; wget http://ftp.drupal.org/files/projects/${DRUPAL_VERSION}.tar.gz -P /var/www/html \
    && echo "${DRUPAL_SHA}  ${DRUPAL_VERSION}.tar.gz" | sha256sum -c - | grep "OK" \
    && tar xzvf /var/www/html/${DRUPAL_VERSION}.tar.gz -C /var/www/html --skip-old-files --strip-components 1 \
    && rm -rfv /var/www/html/${DRUPAL_VERSION}.tar.gz \
    && cp /var/www/html/sites/default/default.settings.php /var/www/html/sites/settings.php \
    && cp /var/www/html/sites/default/default.services.yml /var/www/html/sites/services.yml \
    && chmod 666 /var/www/html/sites/settings.php /var/www/html/sites/services.yml \
    && mkdir /var/www/html/sites/files \
    && chmod 777 /var/www/html/sites/files \
    && chown -R nobody:nogroup \
      /var/www/html/sites/default \
      /var/www/html/themes \
      /var/www/html/modules
VOLUME /var/www/html
