# Inspired by https://github.com/voxxit/dockerfiles/blob/master/consul/Dockerfile
FROM jalaziz/base:alpine

ENV CONSUL_VERSION 0.5.2

RUN  apk add -U make go git gcc musl-dev openssl-dev \
  && export GOPATH=/go \
  && go get -u -v github.com/hashicorp/consul \
  && cd /go/src/github.com/hashicorp/consul \
  && git checkout v${CONSUL_VERSION} \
  && make \
  && mv bin/consul /usr/local/bin/ \
  && rm -rf /go \
  && wget https://dl.bintray.com/mitchellh/consul/${CONSUL_VERSION}_web_ui.zip \
  && unzip ${CONSUL_VERSION}_web_ui.zip \
  && mv dist /ui \
  && rm -f ${CONSUL_VERSION}_web_ui.zip \
  && apk del make go git gcc musl-dev openssl-dev \
  && rm -rf /var/cache/apk/*

ENV GOMAXPROCS 2

EXPOSE 8300 8301 8301/udp 8302 8302/udp 8400 8500 8600 8600/udp

VOLUME [ "/data", "/config" ]

ENTRYPOINT [ "/usr/local/bin/consul" ]
CMD [ "agent", "--data-dir=/data", "--config-dir=/config", "--ui-dir=/ui" ]

