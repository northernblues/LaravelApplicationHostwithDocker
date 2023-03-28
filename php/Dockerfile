FROM php:7.4-fpm

WORKDIR /var/www/html

RUN apt-get update && \
    apt-get install -y --no-install-recommends libzip-dev libonig-dev libpq-dev && \
    docker-php-ext-install pdo_mysql zip opcache && \
    pecl install redis && \
    docker-php-ext-enable redis && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

COPY ./src /var/www/html/src

CMD ["php-fpm"]
