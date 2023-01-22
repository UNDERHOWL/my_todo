FROM php:8.2-fpm

ENV TZ Asia/Tokyo

RUN apt-get update && \
	apt-get install -y git unzip libzip-dev libicu-dev libonig-dev && \
	docker-php-ext-install intl pdo_mysql zip bcmath

RUN pecl install xdebug-3.2.0 && \
    docker-php-ext-enable xdebug

COPY ./docker/app/php.ini /usr/local/etc/php/php.ini

COPY --from=composer:2.0 /usr/bin/composer /usr/bin/composer

COPY ./src /var/www/html

WORKDIR /var/www/html

RUN chmod -R 777 storage
RUN chmod -R 777 bootstrap/cache