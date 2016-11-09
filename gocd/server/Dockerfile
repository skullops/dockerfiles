FROM wizdevops/java:8-alpine
MAINTAINER Daniel Andrei Minca <mandrei17@gmail.com>
# Metadata params
ARG BUILD_DATE
ARG VERSION
ARG VCS_URL
ARG VCS_REF
ENV GOCD_VERSION="16.11.0" \
    SHACHECK="c8fa2dc52dd4797d8f2aa85823f8896dc4d89ee77b3b23925c93afd885080875"
LABEL org.label-schema.build-date=$BUILD_DATE \
      org.label-schema.vcs-url=$VCS_URL \
      org.label-schema.vcs-ref=$VCS_REF \
      org.label-schema.version=$VERSION \
      org.label-schema.name='go.cd server' \
      org.label-schema.description='go.cd server on Alpine Linux optimized for simplicity' \
      org.label-schema.usage='https://github.com/WizDevOps/dockerfiles' \
      org.label-schema.url='https://github.com/WizDevOps/dockerfiles' \
      org.label-schema.vendor='Daniel Andrei Minca' \
      org.label-schema.schema-version='1.0' \
      org.label-schema.docker.cmd='docker run --rm wizdevops/gocdserver' \
      org.label-schema.docker.cmd.devel='docker run --rm -ti wizdevops/gocdserver ash' \
      org.label-schema.docker.debug='docker logs $CONTAINER' \
      io.github.dminca.docker.dockerfile="/Dockerfile" \
      io.github.dminca.license="GPLv3"
RUN set -x \
    && apk add --update --no-cache \
        curl \
        bash \
    && curl -sSL https://download.go.cd/binaries/${VERSION}/generic/go-server-${VERSION}.zip > /tmp/go-server-${VERSION}.zip \
    && unzip /tmp/go-server-${VERSION}.zip -d /tmp \
    && cd /tmp; echo "${SHACHECK}  go-server-16.11.0-4185.zip" | sha256sum -c - | grep OK; cd /\
    && mkdir /etc/go-server \
    && cp -vr /tmp/go-server-${GOCD_VERSION}/* /etc/go-server \
    && rm -rfv /tmp/*
EXPOSE 8154 8153
CMD ["/etc/go-server/server.sh"]
