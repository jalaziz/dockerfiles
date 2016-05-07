FROM jalaziz/base:alpine

RUN  apk add --update python py-pip groff less \
  && pip install awscli \
  && apk del py-pip \
  && rm -rf /var/cache/apk/*

ENTRYPOINT [ "/usr/bin/aws" ]
