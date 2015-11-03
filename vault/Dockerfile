# Inspired by https://github.com/voxxit/dockerfiles/blob/master/vault/Dockerfile
FROM jalaziz/base:alpine

ENV VAULT_VERSION 0.3.1

RUN  apk update \
  && wget -q https://circle-artifacts.com/gh/andyshinn/alpine-pkg-glibc/6/artifacts/0/home/ubuntu/alpine-pkg-glibc/packages/x86_64/glibc-2.21-r2.apk -O /tmp/glibc-2.21-r2.apk \
  && apk add --allow-untrusted /tmp/glibc-2.21-r2.apk \
  && wget -q https://circle-artifacts.com/gh/andyshinn/alpine-pkg-glibc/6/artifacts/0/home/ubuntu/alpine-pkg-glibc/packages/x86_64/glibc-bin-2.21-r2.apk -O /tmp/glibc-bin-2.21-r2.apk \
  && apk add --allow-untrusted /tmp/glibc-bin-2.21-r2.apk \
  && rm -rf /tmp/glibc* \
  && wget -q https://dl.bintray.com/mitchellh/vault/vault_${VAULT_VERSION}_linux_amd64.zip \
  && unzip vault_${VAULT_VERSION}_linux_amd64.zip \
  && mv vault /usr/local/bin/ \
  && rm -f vault_${VAULT_VERSION}_linux_amd64.zip \
  && rm -rf /var/cache/apk/*

EXPOSE 8200

VOLUME [ "/config" ]

ENTRYPOINT [ "/usr/local/bin/vault" ]
CMD [ "server", "-config=/config" ]

