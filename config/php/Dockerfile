FROM php:7.4-fpm

RUN apt-get update && apt-get install -y --no-install-recommends \
        sudo \
        curl \
        wget \
        git \
        unzip \
        zip \
        mc \
        locales \
        libmemcached-dev \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmagickwand-dev \
        graphicsmagick \
        libtidy-dev \
        imagemagick \
        libpng-dev \
		libzip-dev \
        libicu-dev \
    && docker-php-ext-install -j$(nproc) iconv intl tidy mysqli pdo_mysql zip \
    && docker-php-ext-configure gd --with-jpeg=/usr/include/ --with-freetype=/usr/include/ \
    && pecl install memcached \
    && docker-php-ext-enable memcached \    
    && pecl install imagick \
    && docker-php-ext-enable imagick \
    && pecl install redis \
    && docker-php-ext-enable redis \
    && docker-php-ext-enable tidy \
    && docker-php-ext-install -j$(nproc) gd \

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN sed -i '/ru_RU.UTF-8/s/^# //g' /etc/locale.gen && \
    locale-gen \

ENV LANG ru_RU.UTF-8
ENV LC_ALL ru_RU.UTF-8

WORKDIR /var/www/project

CMD ["php-fpm"]
