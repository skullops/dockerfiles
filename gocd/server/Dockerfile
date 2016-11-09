FROM wizdevops/java:8-alpine
MAINTAINER Daniel Andrei Minca <mandrei17@gmail.com>
# Metadata params
ARG BUILD_DATE
ARG VERSION
ARG VCS_URL
ARG VCS_REF
ENV GOCD_VERSION="16.11.0-4185"
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
    && curl -sSL https://download.go.cd/binaries/${GOCD_VERSION}/generic/go-server-${GOCD_VERSION}.zip > /tmp/go-server-${GOCD_VERSION}.zip \
    && mkdir /etc/go \
    && unzip /tmp/go-server-${GOCD_VERSION}.zip -d /etc/go \
    && rm -rfv /tmp/go-server-${GOCD_VERSION}.zip \
    && ln -sv /usr/bin/go-start /etc/go/server.sh \
    && ln -sv /usr/bin/go-stop /etc/go/stop-server.sh
EXPOSE 8154 8153
CMD ["go-start"]
