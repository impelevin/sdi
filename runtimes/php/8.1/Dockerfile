FROM php:8.1-fpm

ARG WWWGROUP
ENV DEBCONF_NOWARNINGS yes

WORKDIR /src

# For composer
RUN apt-get update \
    && apt-get install -y libzip-dev zlib1g-dev gosu \
    && docker-php-ext-install zip

# Install composer
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
    && php composer-setup.php \
    && php -r "unlink('composer-setup.php');" \
    && mv composer.phar /usr/local/bin/composer

# Set composer environment
ENV COMPOSER_ALLOW_SUPERUSER 1
ENV COMPOSER_HOME /composer
ENV PATH $PATH:/composer/vendor/bin

# PHP's DB setting
RUN apt-get update \
    && apt-get install -y libpq-dev libfreetype6-dev libjpeg62-turbo-dev libpng-dev libjpeg-dev
RUN docker-php-ext-install gd pdo_mysql pdo_pgsql

# Install Node.js
RUN apt-get install -y gnupg
RUN curl -sL https://deb.nodesource.com/setup_16.x | bash - \
    && apt-get update \
    && apt-get install -y nodejs

COPY php.ini /etc/php/8.1/cli/conf.d/99-sail.ini

# Add user for application
RUN groupadd -g 1000 www
RUN useradd -u 1000 -ms /bin/bash -g www www

# Change current user to www
USER www

# Expose port 9000 and start php-fpm server
EXPOSE 9000
CMD ["php-fpm"]
