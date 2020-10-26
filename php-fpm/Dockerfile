ARG VERSION
FROM php:${VERSION}-fpm

RUN set -xe; \
    apt-get update && apt-get upgrade -y; \
    apt-get install -yqq \
        curl \
        zip \
        unzip \
        libmemcached-dev \
        libz-dev \
        libpq-dev \
        libjpeg-dev \
        libpng-dev \
        libfreetype6-dev \
        libssl-dev \
        libmcrypt-dev \
        libonig-dev \
        libzip-dev; \
    docker-php-ext-configure gd \
        --prefix=/usr \
        --with-jpeg \
        --with-freetype; \
    docker-php-ext-install gd; \
    docker-php-ext-configure zip; \
    docker-php-ext-install pdo_mysql pdo_pgsql zip; \
    apt-get purge -y --auto-remove; \
    rm -rf /var/cache/apt/* && rm -rf /var/lib/apt/lists/*;

COPY ./php7.4.ini /usr/local/etc/conf.d/php.ini

WORKDIR /var/www

CMD [ "php-fpm" ]

EXPOSE 9000