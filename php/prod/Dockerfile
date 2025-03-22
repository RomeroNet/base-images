FROM php:8.4.5-fpm

RUN apt-get update && apt-get upgrade -y \
    && rm -rf /var/lib/apt/lists/*

RUN docker-php-ext-install bcmath pdo pdo_mysql

WORKDIR /app
