FROM php:8.2-fpm-alpine

RUN apk update && apk add git \
    curl \
    zip \
    unzip \
    mariadb-dev \
    libzip-dev \
    libpng-dev \
    libxml2-dev \
    oniguruma-dev \
    freetype-dev \
    libjpeg-turbo-dev

RUN docker-php-ext-configure gd --with-freetype && docker-php-ext-install pdo pdo_mysql zip gd xml mbstring


# Get latest Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Run composer install in the appropriate directory
WORKDIR /var/www/laravel


COPY docker/php/start-container /usr/local/bin/start-container
RUN chmod +x /usr/local/bin/start-container


ENTRYPOINT ["/usr/local/bin/start-container"]


