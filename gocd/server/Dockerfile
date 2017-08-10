FROM wizdevops/java:8-alpine
MAINTAINER Daniel Andrei Minca <mandrei17@gmail.com>
# Metadata params
ARG BUILD_DATE
ARG VERSION=${VERSION:-"17.8.0-5277"}
ARG VCS_URL
ARG VCS_REF
ENV GOCD_VERSION="17.8.0" \
    SHACHECK="6764cd8c3f13824f892140464d1d50b753d9c1f3782ae38586303d59e296294e" \
    AGPORT=8154 \
    SRVPORT=8153
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
        git \
    && curl -sSL https://download.go.cd/binaries/${VERSION}/generic/go-server-${VERSION}.zip > /tmp/go-server-${VERSION}.zip \
    && mkdir /etc/go-server \
    && unzip /tmp/go-server-${VERSION}.zip -d /tmp \
    && cd /tmp; echo "${SHACHECK}  go-server-${VERSION}.zip" | sha256sum -c - | grep OK; cd /\
    && cp -vr /tmp/go-server-${GOCD_VERSION}/* /etc/go-server \
    && rm -rfv /tmp/*
EXPOSE ${AGPORT} ${SRVPORT}
CMD ["/etc/go-server/server.sh"]
