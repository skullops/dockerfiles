FROM wizdevops/alpine
# Metadata params
ARG BUILD_DATE
ARG VERSION
ARG VCS_URL
ARG VCS_REF
LABEL org.label-schema.build-date=$BUILD_DATE \
      org.label-schema.vcs-url=$VCS_URL \
      org.label-schema.vcs-ref=$VCS_REF \
      org.label-schema.version=$VERSION \
      org.label-schema.name='Monit monitoring' \
      org.label-schema.description='Monit is a small Open Source utility for \
managing and monitoring Unix systems. Monit conducts automatic maintenance and \
repair and can execute meaningful causal actions in error situations.' \
      org.label-schema.usage='https://github.com/WizDevOps/dockerfiles' \
      org.label-schema.url='https://github.com/WizDevOps/dockerfiles' \
      org.label-schema.vendor='Daniel Andrei Minca' \
      org.label-schema.schema-version='1.0' \
      org.label-schema.docker.cmd='docker run --rm wizdevops/monit' \
      org.label-schema.docker.cmd.devel='docker run --rm -ti wizdevops/monit ash' \
      org.label-schema.docker.debug='docker logs $CONTAINER' \
      io.github.dminca.docker.dockerfile="/Dockerfile" \
      io.github.dminca.license="GPLv3" \
      MAINTAINER="Minca Daniel Andrei <mandrei17@gmail.com>"
ENV MONIT_VERSION="5.23.0"
ENV BUILD_PACKAGES="\
  curl \
  build-base \
  zlib-dev \
  linux-pam-dev \
  linux-headers" \
  MONIT_URL="https://mmonit.com/monit/dist/monit-$MONIT_VERSION.tar.gz"

RUN set -x \
    && apk add --update --no-cache --virtual build-deps $BUILD_PACKAGES dumb-init \
    && curl -o /tmp/monit.tar.gz $MONIT_URL \
    && mkdir -p /etc/monit /tmp/monit-source \
    && tar xf /tmp/monit.tar.gz --strip-components=1 -C /tmp/monit-source \
    && cd /tmp/monit-source; ./configure --without-ssl; cd / \
    && make -C /tmp/monit-source/ \
    && make install -C /tmp/monit-source/ \

      # remove build dependencies
      && apk del --purge build-deps \

    && cp /tmp/monit-source/monitrc /etc/monit/monitrc-default \
    && cp /tmp/monit-source/monit /etc/monit \
    && chown root:root /etc/monit/monitrc-default \
    && ln -s /etc/monit/monit /usr/bin/monit \
    && rm -rf /tmp/*
ADD ./monitrc /monitrc
EXPOSE 2812
CMD ["dumb-init","monit", "-d", "10", "-Ic","./monitrc"]
