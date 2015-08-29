# Inspired by https://github.com/voxxit/dockerfiles/blob/master/consul/Dockerfile
FROM jalaziz/base:alpine

ENV CONSUL_VERSION 0.5.2

RUN  wget https://dl.bintray.com/mitchellh/consul/${CONSUL_VERSION}_linux_amd64.zip \
  && unzip ${CONSUL_VERSION}_linux_amd64.zip \
  && mv consul /usr/local/bin/ \
  && rm -f ${CONSUL_VERSION}_linux_amd64.zip \
  && wget https://dl.bintray.com/mitchellh/consul/${CONSUL_VERSION}_web_ui.zip \
  && unzip ${CONSUL_VERSION}_web_ui.zip \
  && mv dist /ui \
  && rm -f ${CONSUL_VERSION}_web_ui.zip

ENV GOMAXPROCS 2

EXPOSE 8300 8301 8301/udp 8302 8302/udp 8400 8500 8600 8600/udp

VOLUME [ "/data", "/config" ]

ENTRYPOINT [ "/usr/local/bin/consul" ]
CMD [ "agent", "--data-dir=/data", "--config-dir=/config", "--ui-dir=/ui" ]

