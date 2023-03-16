FROM php:8.2-alpine

RUN apk --update --no-cache add \
    git \
    curl \
    libmcrypt-dev \
    libxml2-dev \
    libzip-dev \
    oniguruma-dev \
    unzip \
    && docker-php-ext-install \
    bcmath \
    pdo_mysql \
    zip

# Set working directory
WORKDIR /var/www/html

# git clone project
RUN git clone https://github.com/mmkhakdaman/news-aggregator-backend.git .

# install php composer
RUN php -r "readfile('https://getcomposer.org/installer');" | php -- --install-dir=/usr/bin/ --filename=composer

# Install dependencies
RUN COMPOSER_ALLOW_SUPERUSER=1 composer install --no-dev --no-interaction

# Set permissions
RUN chown -R www-data:www-data /var/www/html && \
    chmod -R 775 /var/www/html/storage /var/www/html/bootstrap/cache


