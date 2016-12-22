FROM wizdevops/ant
MAINTAINER Minca Daniel Andrei <mandrei17@gmail.com>
# Metadata params
ARG BUILD_DATE
ARG VERSION
ARG VCS_URL
ARG VCS_REF
ENV CASSANDRA_URL="http://apache.javapipe.com/cassandra/3.9/apache-cassandra-3.9-bin.tar.gz"
LABEL org.label-schema.build-date=$BUILD_DATE \
      org.label-schema.vcs-url=$VCS_URL \
      org.label-schema.vcs-ref=$VCS_REF \
      org.label-schema.version=$VERSION \
      org.label-schema.name='Cassandra Docker image' \
      org.label-schema.description='Cassandra running on Alpine Linux' \
      org.label-schema.usage='https://github.com/WizDevOps/dockerfiles' \
      org.label-schema.url='https://github.com/WizDevOps/dockerfiles' \
      org.label-schema.vendor='Daniel Andrei Minca' \
      org.label-schema.schema-version='1.0' \
      org.label-schema.docker.cmd='docker run --rm wizdevops/cassandra' \
      org.label-schema.docker.cmd.devel='docker run --rm -ti wizdevops/cassandra ash' \
      org.label-schema.docker.debug='docker logs $CONTAINER' \
      io.github.dminca.docker.dockerfile="/Dockerfile" \
      io.github.dminca.license="GPLv3"
RUN set -x \
  
  # download and build
  && apk add --update git \
  && mkdir /build \
  && git clone -b cassandra-3.9 https://github.com/apache/cassandra.git /build \
  && cd /build; ant
