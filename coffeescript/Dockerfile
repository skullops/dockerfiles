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
      org.label-schema.name='Coffeescript Docker Image' \
      org.label-schema.description='The slimest Coffeescript docker image ever seen' \
      org.label-schema.usage='https://github.com/WizDevOps/dockerfiles' \
      org.label-schema.url='https://github.com/WizDevOps/dockerfiles' \
      org.label-schema.vendor='Daniel Andrei Minca' \
      org.label-schema.schema-version='1.0' \
      org.label-schema.docker.cmd='docker run --rm wizdevops/coffeescript' \
      org.label-schema.docker.cmd.devel='docker run --rm -ti wizdevops/coffeescript ash' \
      org.label-schema.docker.debug='docker logs $CONTAINER' \
      io.github.dminca.docker.dockerfile="/Dockerfile" \
      io.github.dminca.license="GPLv3" \
			MAINTAINER="Minca Daniel Andrei <mandrei17@gmail.com>"

ENV NODE_VERSION=v6.10.0 \
		NPM_VERSION=3

RUN set -x \
		&&  apk upgrade --update \
    && apk add --update git curl make gcc g++ python linux-headers libgcc libstdc++ \
    && curl -sSL https://nodejs.org/dist/${NODE_VERSION}/node-${NODE_VERSION}.tar.gz | tar -xz \
    && cd /node-${NODE_VERSION} \
    && ./configure --prefix=/usr --without-snapshot \
    && make -j$(grep -c ^processor /proc/cpuinfo 2>/dev/null || 1) \
    && make install \
    && cd / \
    && npm install -g \
			npm@${NPM_VERSION} \
			coffee-script \
    && apk del gcc g++ linux-headers \
    && rm -rf /etc/ssl /node-${NODE_VERSION} /usr/include \
    /usr/share/man /tmp/* /var/cache/apk/* /root/.npm /root/.node-gyp \
    /usr/lib/node_modules/npm/man /usr/lib/node_modules/npm/doc /usr/lib/node_modules/npm/html
