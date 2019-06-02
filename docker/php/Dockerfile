FROM php:7.2.4-fpm

RUN apt-get update && apt-get install --assume-yes apt-utils
RUN apt-get install -y \
            curl \
            wget \
            git \
            libzip-dev \
            expect \
            nano \
            zip \
            && docker-php-ext-configure zip --with-libzip \
            && docker-php-ext-install -j$(nproc) pdo_mysql zip mysqli

# Install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Install plugin for parallel packages installation
RUN php /usr/local/bin/composer global require hirak/prestissimo

# Set working directory PHP
WORKDIR /var/www

# copy files to image
COPY . /var/www

# copy nginx config to image
COPY ./docker/nginx/hosts/. /etc/nginx/conf.d

CMD ["php-fpm"]
