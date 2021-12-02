FROM php:8.1-fpm

# Set working directory
WORKDIR /var/www

# Install dependencies
RUN apt-get update && apt-get install -y \
    build-essential \
    libpng-dev \
    libjpeg62-turbo-dev \
    libfreetype6-dev \
    locales \
    zip \
    jpegoptim optipng pngquant gifsicle libonig-dev \
    libpq-dev \
    vim \
    unzip \
    git \
    curl unzip libzip-dev zip libxslt-dev

# Clear apt cache
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Install required extensions
RUN git clone -b release/5.3.4 https://github.com/phpredis/phpredis.git /usr/src/php/ext/redis
RUN docker-php-ext-install -j5 mbstring zip exif pcntl pdo_pgsql xsl redis
RUN docker-php-ext-configure gd
RUN docker-php-ext-install gd
RUN docker-php-ext-enable redis

# Install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Create user
RUN groupadd -g 1000 www
RUN useradd -u 1000 -ms /bin/bash -g www www

# Copy existing application directory contents
COPY ./src /var/www

# Copy existing application directory permissions
COPY --chown=www:www ./src /var/www

# Change current user to www
USER www

# Expose port 9000 and start the php-fpm server
EXPOSE 9000
CMD ["php-fpm"]