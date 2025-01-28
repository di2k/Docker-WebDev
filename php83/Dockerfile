# Use PHP 8.3 FPM as base image
FROM php:8.3-fpm

# Update package list
RUN apt-get update

# Install dependencies
RUN apt-get install -y libpng-dev libjpeg-dev libfreetype6-dev libxml2-dev libzip-dev zip unzip wget

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Install and enable FFI extension
RUN apt-get install -y libffi-dev \
    && docker-php-ext-install ffi

# Configure and install PHP extensions
RUN docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install gd mysqli pdo pdo_mysql dom zip

# Download and install IonCube Loader for PHP 8.3
RUN wget https://downloads.ioncube.com/loader_downloads/ioncube_loaders_lin_x86-64.tar.gz \
    && tar -xzf ioncube_loaders_lin_x86-64.tar.gz \
    && PHP_EXT_DIR=$(php -i | grep "^extension_dir" | awk '{print $3}') \
    && mv ioncube/ioncube_loader_lin_8.3.so $PHP_EXT_DIR/ \
    && echo "zend_extension=$PHP_EXT_DIR/ioncube_loader_lin_8.3.so" > /usr/local/etc/php/conf.d/00-ioncube.ini \
    && rm -rf ioncube* 

# Copy custom PHP configuration (option 1)
#COPY php.ini /usr/local/etc/php/

# OR copy custom config file (option 2)
COPY custom-config.ini /usr/local/etc/php/conf.d/

# Set the working directory
WORKDIR /var/www/html

# Expose port 9000 and start php-fpm server
EXPOSE 9000
