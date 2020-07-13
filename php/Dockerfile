FROM php:7.1-fpm

RUN docker-php-ext-install \
  mbstring \
  pdo \
  gd \
  xml \
  mcrypt \
  zip \
  bcmath

# RUN pecl install -o -f xdebug-2.4.0
RUN pecl install xdebug
RUN docker-php-ext-enable xdebug

COPY php.ini /etc/php/
RUN { \
  echo 'xdebug.remote_enable = On'; \
  echo 'xdebug.remote_autostart = On'; \
  echo 'xdebug.remote_connect_back = 1'; \
  echo 'xdebug.remote_port = 9000'; \
  echo 'xdebug.scream = 0'; \
  echo 'xdebug.show_local_vars = 1'; \
  echo 'xdebug.idekey=PHPSTORM'; \
} > /etc/php.ini

# install composer
RUN cd /usr/bin && curl -s http://getcomposer.org/installer | php && ln -s /usr/bin/composer.phar /usr/bin/composer
RUN apt-get update \
&& apt-get install -y \
git \
zip \
unzip \
vim

RUN apt-get update \
    && apt-get install -y libpq-dev \
    && docker-php-ext-install pdo_mysql pdo_pgsql

WORKDIR /home/docker
