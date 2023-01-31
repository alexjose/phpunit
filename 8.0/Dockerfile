FROM php:8.0-cli

RUN apt install \
    libonig-dev \
    libcurl4-gnutls-dev \
    libicu-dev zlib1g-dev \
    libpng-dev \
    libxml2-dev \
    libzip-dev \
    libgpgme11-dev

RUN docker-php-ext-install \
    mbstring \
    pdo_mysql \
    curl \
    intl \
    gd \
    xml \
    zip

RUN pecl install \
    xdebug \
    redis \
    gnupg

RUN docker-php-ext-enable \
    xdebug \
    redis \
    gnupg

RUN echo "xdebug.mode=coverage" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
RUN echo "memory_limit=512M" > /usr/local/etc/php/conf.d/40-memory-limit.ini

COPY --from=composer:2 /usr/bin/composer /usr/local/bin/composer
