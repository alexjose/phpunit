FROM php:8.2-cli

RUN apt update -y && apt install -y \
    git \
    zip \
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
    zip \
    pcntl

RUN pecl install \
    pcov \
    redis \
    gnupg

RUN docker-php-ext-enable \
    pcov \
    redis \
    gnupg

RUN echo "memory_limit=512M" > /usr/local/etc/php/conf.d/40-memory-limit.ini

COPY --from=composer:2 /usr/bin/composer /usr/local/bin/composer
