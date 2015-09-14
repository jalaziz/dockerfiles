FROM jalaziz/base:alpine

ENV CONSUL_TEMPLATE_VERSION 0.10.0

RUN  wget -qO- https://github.com/hashicorp/consul-template/releases/download/v${CONSUL_TEMPLATE_VERSION}/consul-template_${CONSUL_TEMPLATE_VERSION}_linux_amd64.tar.gz \
      | tar -C /tmp -xz \
  && mv /tmp/consul-template_${CONSUL_TEMPLATE_VERSION}_linux_amd64/consul-template /usr/local/bin \
  && rm -rf /tmp/*

VOLUME [ "/config", "/templates" ]

ENTRYPOINT [ "/usr/local/bin/consul-template" ]
CMD [ "-config=/config" ]
