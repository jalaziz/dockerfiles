# TODO: Compile nginx on Alpine
FROM nginx

RUN rm /etc/nginx/conf.d/default.conf

COPY nginx.conf /etc/nginx/nginx.conf

VOLUME [ "/etc/nginx/conf.d" ]
