FROM jalaziz/base:alpine

RUN apk add --update go \
  && rm -rf /var/cache/apk/*

RUN wget -O /tmp/teeproxy-master.tar.gz https://github.com/chrislusf/teeproxy/archive/master.tar.gz \
  && tar xzf /tmp/teeproxy-master.tar.gz -C /tmp \
  && cd /tmp/teeproxy-master && go build \
  && mv teeproxy-master /usr/local/bin/teeproxy \
  && rm -rf /tmp/*

ENTRYPOINT [ "/usr/local/bin/teeproxy" ]