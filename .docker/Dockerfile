FROM php:8.3-fpm

RUN apt-get update && apt-get install -y \
  libfreetype6-dev \
  libjpeg62-turbo-dev \
  libmcrypt-dev \
  libpng-dev \
  libicu-dev \
  libpq-dev \
  libxpm-dev \
  libvpx-dev \
  libzip-dev
RUN pecl channel-update pecl.php.net \
  && pecl install xdebug \
  && pecl install mcrypt
RUN docker-php-ext-enable xdebug \
  && docker-php-ext-enable mcrypt \
  && docker-php-ext-install -j$(nproc) gd \
  && docker-php-ext-install -j$(nproc) intl \
  && docker-php-ext-install -j$(nproc) zip \
  && docker-php-ext-install -j$(nproc) pgsql \
  && docker-php-ext-install -j$(nproc) pdo_pgsql \
  && docker-php-ext-install -j$(nproc) exif \
  && docker-php-ext-configure gd \
  --with-freetype=/usr/include/ \
  --with-jpeg=/usr/include/ \
  --with-xpm=/usr/lib/x86_64-linux-gnu/