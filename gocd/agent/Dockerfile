FROM wizdevops/java:8-alpine
MAINTAINER Daniel Andrei Minca <mandrei17@gmail.com>
# Metadata params
ARG BUILD_DATE
ARG VERSION
ARG VCS_URL
ARG VCS_REF
ENV GOCD_VERSION="17.8.0-5277" \
    SHACHECK="4c9c220240ee42a189c787c1bd967f36c9d2e63f75fb4019f3f3cc409f4db733"
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
        git \
    && curl -sSL -o /tmp/go-agent.zip https://download.go.cd/binaries/${GOCD_VERSION}/generic/go-agent-${GOCD_VERSION}.zip \
    && mkdir /etc/go-agent \
    && unzip /tmp/go-agent.zip -d /tmp \
    && cd /tmp; echo "${SHACHECK}  go-agent.zip" | sha256sum -c - | grep OK; cd - \
    && cp -vr /tmp/go-agent-${GOCD_VERSION:0:6}/* /etc/go-agent \
    && rm -rfv /tmp/*
CMD ["/etc/go-agent/agent.sh"]
