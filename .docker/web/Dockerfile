FROM php:7-apache

# PHP extension
RUN requirements="zlib1g-dev libicu-dev git curl" \
    && apt-get update && apt-get install -y $requirements && rm -rf /var/lib/apt/lists/* \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-install intl \
    && docker-php-ext-install zip \
    && apt-get purge --auto-remove -y

# Apache & PHP configuration
RUN a2enmod rewrite
ADD apache/vhost.conf /etc/apache2/sites-enabled/000-default.conf
ADD php/php.ini /usr/local/etc/php/php.ini

# Install composer
RUN curl -sS https://getcomposer.org/installer | php \
    && mv composer.phar /usr/bin/composer

# Add the application
ADD . /www
WORKDIR /www

RUN usermod -u 1000 www-data

# Ensure that the production container will run with the www-data user
RUN chown www-data /www

#CMD ["/app/docker/apache/run.sh"]
