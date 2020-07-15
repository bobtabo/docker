FROM php:7.1-fpm

# ライブラリのインストール
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

# Xdebugのインストール
RUN pecl install xdebug
RUN docker-php-ext-enable xdebug

# php.iniの置換
COPY php.ini /etc/php.ini

# Composerのインストール
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# ユーザーを作成
RUN useradd -m -s /bin/bash -u 1000 docker

# ユーザー切り替え
USER  docker

WORKDIR /home/docker
