FROM php:8.1-fpm

RUN apt-get update -y \
  && apt-get install -y libxml2-dev zlib1g-dev libpng-dev libjpeg-dev libfreetype6-dev libzip-dev less zip unzip vim wget git \
  && apt-get clean -y \
  && usermod -u 1000 www-data && groupmod -g 1000 www-data \
  && docker-php-ext-install mysqli \
  && docker-php-ext-install soap \
  && docker-php-ext-install opcache \
  && docker-php-ext-install pdo_mysql \
  && docker-php-ext-install intl \
  && docker-php-ext-install zip

# RUN pecl install xdebug && docker-php-ext-enable xdebug
  
RUN docker-php-ext-configure gd --with-jpeg=/usr/include/ \
    && docker-php-ext-install gd

RUN chown -R www-data:www-data /var/www

RUN wget https://github.com/mailhog/mhsendmail/releases/download/v0.2.0/mhsendmail_linux_amd64 \
    && chmod +x mhsendmail_linux_amd64 \
    && mv mhsendmail_linux_amd64 /usr/local/bin/mhsendmail
    
USER www-data
ENV PS1="\u@\w\\$ "