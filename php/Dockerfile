FROM php:7.1-fpm-alpine

RUN set -e \
    && apk add --no-cache \
       nginx \
       # GD
       freetype libpng libjpeg-turbo \
    && apk add --no-cache --virtual .build-deps \
       # For pulling archive over https
       ca-certificates \
       openssl \
       # For GD (creating thumbnails inside webtrees)
       libpng-dev libjpeg-turbo-dev freetype-dev \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ --with-png-dir=/usr/include/ \
    && docker-php-ext-install \
       gd \
       pdo \
       mysqli \
       pdo_mysql
#    && apk del .build-deps \