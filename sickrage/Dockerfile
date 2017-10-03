FROM alpine:3.5
MAINTAINER VictorPiolin ( victorpiolin@gmail.com )

### Install Sickrage
RUN apk --no-cache upgrade && \
    apk add --no-cache --virtual=build-deps \
      make \
      gcc \
      g++ \
      python-dev \
      py2-pip \
      libressl-dev \
      libffi-dev && \
    apk add --no-cache --virtual=run-deps \
      ca-certificates \
      python \
      py-libxml2 \
      py-lxml \
      unrar  \
      su-exec \
      git && \
    pip --no-cache-dir install --upgrade setuptools && \
    pip --no-cache-dir install --upgrade pyopenssl cheetah requirements && \
    git clone --depth 1 https://github.com/SickRage/SickRage.git /opt/sickrage && \
    apk del --no-cache --purge \
    build-deps  && \
    rm -rf /opt/sickrage/.git* \
           /tmp/* \
           /var/cache/apk/*  \
           /var/tmp/*

### Volumes
VOLUME [ "/media" ]

### EXPOSES
EXPOSE 8081

COPY default /etc/default/sickrage

CMD [ "/usr/bin/python", "/opt/sickrage/SickBeard.py", "--datadir=/config", "--config=/config/config.ini" ]
