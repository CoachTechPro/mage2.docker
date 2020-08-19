FROM pagespeed/nginx-pagespeed
LABEL maintainer="Osiozekhai Aliu"
COPY conf/nginx.conf /etc/nginx/nginx.conf
COPY conf/default.conf /etc/nginx/conf.d/default.conf
COPY conf/default_ssl.conf /etc/nginx/conf.d/default_ssl.conf
COPY docker-entrypoint.sh /usr/local/bin
RUN chmod +x /usr/local/bin/docker-entrypoint.sh \
    && echo http://dl-2.alpinelinux.org/alpine/edge/community/ >> /etc/apk/repositories \
    && apk add --update netcat-openbsd shadow bc curl wget git nano bash openssl tzdata libressl \
    && apk add python3 python3-dev build-base libressl-dev musl-dev libffi-dev \
    && pip3 install pip --upgrade \
    && pip3 install certbot-nginx \
    && mkdir /etc/letsencrypt \
    && apk -v cache clean \
    && rm -rf /var/cache/apk/*;
