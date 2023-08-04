FROM php:8.2-fpm-alpine

# Update index
RUN apk update

# Install bash
RUN apk add bash

#Install packages
# RUN apk add --no-cache libpng libpng-dev 

# Install extensions
RUN docker-php-ext-install pdo_mysql 

# Copy bash config
COPY .bashrc /home/user/.bashrc

# Install Composer
COPY --from=composer:latest /usr/bin/composer /usr/local/bin/composer

# Configure PHP
COPY php.ini $PHP_INI_DIR/conf.d/opcache.ini

# Use the default development configuration
RUN mv $PHP_INI_DIR/php.ini-development $PHP_INI_DIR/php.ini

# Create user based on provided user ID
ARG HOST_UID
RUN adduser --disabled-password --gecos "" --uid $HOST_UID user

# Switch to that user
USER user
