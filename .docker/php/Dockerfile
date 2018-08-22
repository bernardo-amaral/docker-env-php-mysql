FROM php:7-apache

RUN apt-get update 

RUN apt-get install -y curl build-essential apt-transport-https libc6 libstdc++6
RUN apt-get install -y locales \ 
    && echo "en_US.UTF-8 UTF-8" > /etc/locale.gen \ 
    && locale-gen

RUN apt-get install -y libpng-dev libjpeg-dev libfreetype6-dev
RUN apt-get install -y libmcrypt-dev
RUN apt-get install -y libreadline-dev
RUN apt-get install -y libpq-dev
RUN apt-get install -y mysql-client
RUN apt-get install -y libxml2-dev

RUN docker-php-ext-install pdo soap bcmath pdo_mysql mbstring mysqli gd iconv zip

ADD . /app

RUN echo "include /app/.docker/php/apache2.conf" >> /etc/apache2/apache2.conf
RUN ln -sf /app/.docker/php/app.conf /etc/apache2/sites-enabled/app.conf
RUN ln -sf /app/.docker/php/php.ini /usr/local/etc/php/conf.d/99-app.ini
RUN rm /etc/apache2/sites-enabled/000-default.conf

RUN a2enmod rewrite
RUN a2enmod ssl

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

WORKDIR /app
VOLUME ["/app"]

RUN mkdir /etc/apache2/ssl
RUN openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/apache2/ssl/apache.key -out /etc/apache2/ssl/apache.crt \
    -subj "/C=BR/ST=RS/L=Porto Alegre/O=TJ/OU=IT Department/CN=bernardo-amaral.com.br/"

ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR /var/log/apache2

#EXPOSE 80 443
CMD ["apache2-foreground"]
