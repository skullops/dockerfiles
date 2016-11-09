FROM wizdevops/java:8-alpine
MAINTAINER Daniel Andrei Minca <mandrei17@gmail.com>
# Metadata params
ARG BUILD_DATE
ARG VERSION=${VERSION:-"16.11.0-4185"}
ARG VCS_URL
ARG VCS_REF
ENV GOCD_VERSION="16.11.0" \
    SHACHECK="2d1d750be75340a6e87058be91c8a0af2187985bef916d4901b03e06875d5bd1"
LABEL org.label-schema.build-date=$BUILD_DATE \
      org.label-schema.vcs-url=$VCS_URL \
      org.label-schema.vcs-ref=$VCS_REF \
      org.label-schema.version=$VERSION \
      org.label-schema.name='go.cd agent' \
      org.label-schema.description='go.cd agent on Alpine Linux optimized for simplicity' \
      org.label-schema.usage='https://github.com/WizDevOps/dockerfiles' \
      org.label-schema.url='https://github.com/WizDevOps/dockerfiles' \
      org.label-schema.vendor='Daniel Andrei Minca' \
      org.label-schema.schema-version='1.0' \
      org.label-schema.docker.cmd='docker run --rm wizdevops/gocdagent' \
      org.label-schema.docker.cmd.devel='docker run --rm -ti wizdevops/gocdagent ash' \
      org.label-schema.docker.debug='docker logs $CONTAINER' \
      io.github.dminca.docker.dockerfile="/Dockerfile" \
      io.github.dminca.license="GPLv3"
RUN set -x \
    && apk add --update --no-cache \
        curl \
        bash \
    && curl -sSL https://download.go.cd/binaries/${VERSION}/generic/go-agent-${VERSION}.zip > /tmp/go-agent-${VERSION}.zip \
    && mkdir /etc/go-agent \
    && unzip /tmp/go-agent-${VERSION}.zip -d /tmp \
    && cd /tmp; echo "${SHACHECK}  go-agent-${VERSION}.zip" | sha256sum -c - | grep OK; cd / \
    && cp -vr /tmp/go-agent-${GOCD_VERSION}/* /etc/go-agent \
    && rm -rfv /tmp/*
CMD ["/etc/go-agent/agent.sh"]
