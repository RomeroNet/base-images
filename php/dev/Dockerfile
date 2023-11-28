FROM php:8.3.0-fpm

WORKDIR /app

RUN apt-get update && apt-get install -y \
    unzip \
    git \
    && apt-get upgrade -y \
    && rm -rf /var/lib/apt/lists/*

RUN docker-php-ext-install bcmath pdo pdo_mysql

RUN pecl install xdebug \
    && docker-php-ext-enable xdebug

COPY --from=composer:2.6.5 /usr/bin/composer /usr/bin/composer
COPY xdebug.ini /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
