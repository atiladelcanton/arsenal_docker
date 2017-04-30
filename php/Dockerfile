FROM php:7.1-apache

MAINTAINER Átila Delcanton Rampazo <atilarampazo@gmail.com>

RUN apt-get update && apt-get install -y nano git curl npm

RUN rm /etc/localtime
RUN ln -s /usr/share/zoneinfo/America/Sao_Paulo /etc/localtime

RUN docker-php-ext-install pdo pdo_mysql opcache

ENV COMPOSER_HOME /composer
ENV PATH /composer/vendor/bin:$PATH
ENV COMPOSER_ALLOW_SUPERUSER 1

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN php composer-setup.php
RUN php -r "unlink('composer-setup.php');"
RUN php composer.phar --install-dir=bin --filename=composer
RUN mv composer.phar /usr/local/bin/composer
RUN npm install -g gulp

EXPOSE 80