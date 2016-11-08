# -----------------------------------------------------------------------------
# INSTALL PACKER BY HASHICORP
# -----------------------------------------------------------------------------
FROM wizdevops/alpine
MAINTAINER Daniel Andrei Minca <@dminca>
# Metadata params
ARG BUILD_DATE
ARG VERSION
ARG VCS_URL
ARG VCS_REF
LABEL org.label-schema.build-date=$BUILD_DATE \
      org.label-schema.vcs-url=$VCS_URL \
      org.label-schema.vcs-ref=$VCS_REF \
      org.label-schema.version=$VERSION \
      org.label-schema.name='Packer by HashiCorp' \
      org.label-schema.description='Packer by HashiCorp on Alpine Linux for \
creating machine and container images for multiple platforms from a single \
source configuration' \
      org.label-schema.usage='https://github.com/WizDevOps/dockerfiles' \
      org.label-schema.url='https://github.com/WizDevOps/dockerfiles' \
      org.label-schema.vendor='Daniel Andrei Minca' \
      org.label-schema.schema-version='1.0' \
      org.label-schema.docker.cmd='docker run --rm wizdevops/packer' \
      org.label-schema.docker.cmd.devel='docker run --rm -ti wizdevops/packer ash' \
      org.label-schema.docker.debug='docker logs $CONTAINER' \
      io.github.dminca.docker.dockerfile="/Dockerfile" \
      io.github.dminca.license="GPLv3"
RUN set -x \
      && mkdir /tmp/packer \
      && cd /tmp/packer \
      && apk add --update --no-cache \
            bash \
            curl \
            ca-certificates \
            openssh-client \
            git \
            unzip \
      && curl -sSLO https://releases.hashicorp.com/packer/${VERSION}/packer_${VERSION}_linux_amd64.zip \
      && unzip packer_${VERSION}_linux_amd64.zip \
      && apk del unzip \
      && mv -v packer* /usr/bin \
      && rm -rf /var/cache/apk/* \
      && rm -rf /tmp/packer

ENTRYPOINT ["packer"]
