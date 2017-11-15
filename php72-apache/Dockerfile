FROM php:rc-apache

MAINTAINER sakadonohitio

RUN apt-get update && apt-get install -y && \
    docker-php-ext-install pdo pdo_mysql mysqli

ADD conf/general.ini /usr/local/etc/php/conf.d/general.ini
ADD conf/mbstring.ini /usr/local/etc/php/conf.d/mbstring.ini
ADD conf/timezone.ini /usr/local/etc/php/conf.d/timezone.ini
