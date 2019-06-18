FROM php:7-fpm-alpine

RUN apk add --no-cache zip \
    unzip \
    zlib-dev \
    libzip-dev \
    libpq \
    postgresql-dev \
    curl \
    git

RUN docker-php-ext-install zip \
    bcmath \
    pgsql \ 
    pdo_pgsql

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN apk add shadow && usermod -u 1000 www-data && groupmod -g 1000 www-data

WORKDIR /var/www/app

CMD composer install

CMD php artisan key:generate
CMD php artisan migrate
CMD php artisan db:seed

CMD php-fpm






