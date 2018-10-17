# FROM php:7.1-fpm
ARG PHP_VERSION

FROM php:${PHP_VERSION}-fpm
# FROM laradock/php-fpm:2.2-${PHP_VERSION}

RUN usermod -u 1000 www-data

RUN apt-get update \
    && apt-get install -y --no-install-recommends \ 
    curl \
    libmemcached-dev \
    libz-dev \
    libpq-dev \
    libjpeg-dev \
    libfreetype6-dev \
    libssl-dev \
    libmcrypt-dev \
    libkrb5-dev \
    libc-client-dev \
    iputils-ping \
    zlib1g-dev \
    libicu-dev \
    g++ \
    && rm -rf /var/lib/apt/lists/* \
    && docker-php-ext-install mcrypt \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-configure intl \
    && docker-php-ext-install intl \
    && docker-php-ext-configure gd \
        --enable-gd-native-ttf \
        --with-jpeg-dir=/usr/lib \
        --with-freetype-dir=/usr/include/freetype2 \
    && docker-php-ext-install gd


## ZIP ##
ARG PHP_INSTALL_ZIP
RUN if [ ${PHP_INSTALL_ZIP} = true ]; then \
    docker-php-ext-install zip \
;fi

## BCMATH ##
ARG PHP_INSTALL_BCMATH
RUN if [ ${PHP_INSTALL_BCMATH} = true ]; then \
    docker-php-ext-install bcmath \
;fi

ARG PHP_INSTALL_MYSQLI
RUN if [ ${PHP_INSTALL_MYSQLI} = true ]; then \
    docker-php-ext-install mysqli \
;fi

## IMAP ##
ARG PHP_INSTALL_IMAP
RUN if [ ${PHP_INSTALL_IMAP} = true ]; then \
    docker-php-ext-configure imap --with-kerberos --with-imap-ssl && \
    docker-php-ext-install imap \
;fi


RUN cp /usr/local/etc/php/php.ini-production /usr/local/etc/php/php.ini && \
    sed -i "s/\;date.timezone =/date.timezone='Europe\/Madrid'/" /usr/local/etc/php/php.ini

WORKDIR /var/www

