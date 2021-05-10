# php7.4を使用する
FROM php:7.4-fpm-buster
SHELL ["/bin/bash", "-oeux", "pipefail", "-c"]

ENV COMPOSER_ALLOW_SUPERUSER=1 \
  COMPOSER_HOME=/composer

COPY --from=composer:1.10 /usr/bin/composer /usr/bin/composer

RUN apt-get update
RUN apt-get -y install git unzip libzip-dev libicu-dev libonig-dev
RUN apt-get clean
RUN rm -rf /var/lib/apt/lists/*
RUN docker-php-ext-install intl pdo_mysql zip bcmath

# iniファイルをアップロード
COPY ./php.ini /usr/local/etc/php/php.ini

# swagger用のファイルを
RUN mkdir /output
RUN mkdir /output/swagger
RUN chmod 777 -R /output
RUN chmod 777 -R /output/swagger

WORKDIR /work
