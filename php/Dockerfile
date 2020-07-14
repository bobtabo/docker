FROM php:7.1-fpm

RUN apt-get update
RUN apt-get install -y \
      sudo \
      libpq-dev \
      git \
      zip \
      unzip \
      vim
RUN docker-php-ext-install \
      bcmath \
      pdo_mysql

# RUN pecl install -o -f xdebug-2.4.0
RUN pecl install xdebug
RUN docker-php-ext-enable xdebug

COPY php.ini /etc/php.ini

# install composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# ユーザーを作成
RUN useradd -m -s /bin/bash -u 1000 docker

WORKDIR /home/docker
