FROM ubuntu

ARG PHP_VERSION

ADD install-composer.sh /usr/bin/install-composer.sh

WORKDIR /var/www

RUN apt-get update && apt install -y apt-utils cron software-properties-common  && \
    echo 'debconf debconf/frontend select Noninteractive' | debconf-set-selections && \
    usermod --uid 1000 --shell /bin/bash www-data  && \
    add-apt-repository -y ppa:ondrej/php && apt-get update && \
    apt install -y --assume-yes wget nano php${PHP_VERSION}-cli  openssl ca-certificates  curl git unzip && \
    install-composer.sh


## MBSTRING ##
ARG PHP_INSTALL_MBSTRING

RUN if [ ${PHP_INSTALL_MBSTRING} = true ]; then \
    apt install -y --assume-yes php${PHP_VERSION}-mbstring \
;fi

## SQLITE3 ##
ARG PHP_INSTALL_SQLITE

RUN if [ ${PHP_INSTALL_SQLITE} = true ]; then \
    apt install -y --assume-yes php${PHP_VERSION}-sqlite3 \
;fi

## XML ##
ARG PHP_INSTALL_XML
RUN if [ ${PHP_INSTALL_XML} = true ]; then \
    apt install -y --assume-yes php${PHP_VERSION}-xml \
;fi

## ZIP ##
ARG PHP_INSTALL_ZIP
RUN if [ ${PHP_INSTALL_ZIP} = true ]; then \
    apt install -y --assume-yes php${PHP_VERSION}-zip \
;fi

## JSON ##
ARG PHP_INSTALL_JSON
RUN if [ ${PHP_INSTALL_JSON} = true ]; then \
    apt install -y --assume-yes php${PHP_VERSION}-json \
;fi

## CURL ##
ARG PHP_INSTALL_CURL
RUN if [ ${PHP_INSTALL_CURL} = true ]; then \
    apt install -y --assume-yes php${PHP_VERSION}-curl \
;fi

## BCMATH ##
ARG PHP_INSTALL_BCMATH
RUN if [ ${PHP_INSTALL_BCMATH} = true ]; then \
    apt install -y --assume-yes php${PHP_VERSION}-bcmath \
;fi


## MYSQLI ##
ARG PHP_INSTALL_MYSQLI
RUN if [ ${PHP_INSTALL_MYSQLI} = true ]; then \
    apt install -y --assume-yes php${PHP_VERSION}-mysqli \
;fi

## IMAP ##
ARG PHP_INSTALL_IMAP
RUN if [ ${PHP_INSTALL_IMAP} = true ]; then \
    apt install -y --assume-yes php${PHP_VERSION}-imap \
;fi