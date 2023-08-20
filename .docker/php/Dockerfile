FROM php:7.4-fpm

RUN apt-get update && apt-get install -y --no-install-recommends \
  nano \
  autoconf \
  build-essential \
  apt-utils \
  zlib1g-dev \
  libzip-dev \
  unzip \
  zip \
  libmagick++-dev \
  libmagickwand-dev \
  libpq-dev \
  libfreetype6-dev \
  libjpeg62-turbo-dev \
  libpng-dev

RUN docker-php-ext-configure gd \
  --with-jpeg=/usr/include/ \
  --with-freetype=/usr/include/

RUN docker-php-ext-configure zip

RUN docker-php-ext-install gd intl pdo_mysql pdo_pgsql mysqli zip \
  && apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*

RUN pecl install imagick-3.4.3

RUN pecl install xdebug-3.1.5 && docker-php-ext-enable xdebug

RUN docker-php-ext-enable imagick

RUN curl -sS https://getcomposer.org/installer | php
RUN mv composer.phar /usr/bin/composer

WORKDIR /var/www/html

EXPOSE 80
