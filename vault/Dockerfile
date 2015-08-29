# Inspired by https://github.com/voxxit/dockerfiles/blob/master/vault/Dockerfile
FROM alpine:edge

ENV VAULT_VERSION 0.2.0

RUN  wget https://dl.bintray.com/mitchellh/vault/vault_${VAULT_VERSION}_linux_amd64.zip \
  && unzip vault_${VAULT_VERSION}_linux_amd64.zip \
  && mv vault /usr/local/bin/ \
  && rm -f vault_${VAULT_VERSION}_linux_amd64.zip

EXPOSE 8200

VOLUME [ "/config" ]

ENTRYPOINT [ "/usr/local/bin/vault" ]
CMD [ "server", "-config=/config" ]

