FROM mediawiki:1.35.1-fpm

# Composer requirements
RUN apt-get update && apt-get install zip unzip libzip-dev  -y \
    && docker-php-ext-configure zip \
    && docker-php-ext-install -j$(nproc) zip

# Install Composer 1
RUN curl -sS https://getcomposer.org/installer | php -- --1 --install-dir=/usr/local/bin --filename=composer

# Install additional Composer dependencies
RUN COMPOSER=composer.local.json composer require --no-update \
  mediawiki/semantic-media-wiki \
  mediawiki/page-forms
RUN composer update --no-dev
