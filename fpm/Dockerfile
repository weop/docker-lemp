FROM ubuntu:18.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y software-properties-common language-pack-en-base \
    && LC_ALL=en_US.UTF-8 add-apt-repository -y ppa:ondrej/php \
    && apt-get update

RUN apt-get install -y mcrypt curl supervisor

RUN apt-get install -y php7.3-fpm mcrypt curl composer \
       php7.3-curl php7.3-mysql \
       php7.3-gd php7.3-redis php7.3-mbstring php7.3-zip php7.3-tokenizer php7.3-zip php7.3-json php7.3-xml \
    && mkdir /run/php

RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf

RUN sed -i -e 's/listen = \/run\/php\/php7.3-fpm.sock/listen = 0.0.0.0:9000/g' /etc/php/7.3/fpm/pool.d/www.conf \
    && sed -i -e 's/;daemonize = yes/daemonize = no/g' /etc/php/7.3/fpm/php-fpm.conf

WORKDIR /var/app

EXPOSE 9000

CMD ["/usr/bin/supervisord"]