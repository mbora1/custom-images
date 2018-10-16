FROM ubuntu

ADD install-composer.sh /usr/bin/install-composer.sh

WORKDIR /var/www

RUN apt-get update && apt-get -y dist-upgrade && apt install -y apt-utils cron  && \
    echo 'debconf debconf/frontend select Noninteractive' | debconf-set-selections && \
    usermod --uid 1000 --shell /bin/bash www-data && \
    apt install -y --assume-yes wget nano php7.2-cli php7.2-mbstring php7.2-sqlite3 php7.2-xml php7.2-json php7.2-zip  openssl ca-certificates  curl git unzip && \
    apt install -y --assume-yes php7.2-curl php7.2-bcmath && \
    install-composer.sh
