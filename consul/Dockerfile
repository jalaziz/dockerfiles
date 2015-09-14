# Inspired by https://github.com/voxxit/dockerfiles/blob/master/consul/Dockerfile
FROM jalaziz/base:alpine

ENV CONSUL_VERSION 0.5.2

RUN  apk update \
  && wget -q https://circle-artifacts.com/gh/andyshinn/alpine-pkg-glibc/6/artifacts/0/home/ubuntu/alpine-pkg-glibc/packages/x86_64/glibc-2.21-r2.apk -O /tmp/glibc-2.21-r2.apk \
  && apk add --allow-untrusted /tmp/glibc-2.21-r2.apk \
  && wget -q https://circle-artifacts.com/gh/andyshinn/alpine-pkg-glibc/6/artifacts/0/home/ubuntu/alpine-pkg-glibc/packages/x86_64/glibc-bin-2.21-r2.apk -O /tmp/glibc-bin-2.21-r2.apk \
  && apk add --allow-untrusted /tmp/glibc-bin-2.21-r2.apk \
  && rm -rf /tmp/glibc* \
  && wget -q https://dl.bintray.com/mitchellh/consul/${CONSUL_VERSION}_linux_amd64.zip \
  && unzip ${CONSUL_VERSION}_linux_amd64.zip \
  && mv consul /usr/local/bin/ \
  && rm -f ${CONSUL_VERSION}_linux_amd64.zip \
  && wget -q https://dl.bintray.com/mitchellh/consul/${CONSUL_VERSION}_web_ui.zip \
  && unzip ${CONSUL_VERSION}_web_ui.zip \
  && mv dist /ui \
  && rm -f ${CONSUL_VERSION}_web_ui.zip \
  && rm -rf /var/cache/apk/*

ENV GOMAXPROCS 2

EXPOSE 8300 8301 8301/udp 8302 8302/udp 8400 8500 8600 8600/udp

VOLUME [ "/data", "/config" ]

ENTRYPOINT [ "/usr/local/bin/consul" ]
CMD [ "agent", "--data-dir=/data", "--config-dir=/config", "--ui-dir=/ui" ]

