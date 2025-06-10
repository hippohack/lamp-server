FROM php:8.4-apache

RUN apt-get update --fix-missing

RUN apt-get -y install \
    libicu-dev \
    libpng-dev \
    msmtp \
    msmtp-mta \
    mailutils \
    libzip-dev \
    zip \
    unzip \
    subversion \
    libapache2-mod-svn \
    default-mysql-client \
    wget

RUN pecl install xdebug
RUN docker-php-ext-enable xdebug

RUN docker-php-ext-configure zip

RUN docker-php-ext-install \
    pdo_mysql \
    pdo \
    mysqli \
    intl \
    gd \
    zip

RUN ln -s /etc/apache2/mods-available/rewrite.load /etc/apache2/mods-enabled/rewrite.load
RUN ln -s /etc/apache2/mods-available/vhost_alias.load /etc/apache2/mods-enabled
RUN echo ServerName $(hostname) > /etc/apache2/conf-available/fqdn.conf && a2enconf fqdn

COPY ./base.conf /etc/apache2/sites-available/base.conf
RUN a2ensite base.conf

COPY ./xdebug.ini /usr/local/etc/php/conf.d/xdebug.ini
COPY ./php.ini /usr/local/etc/php/

# WP-CLI install
RUN curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar
RUN chmod +x wp-cli.phar
RUN mv wp-cli.phar /usr/local/bin/wp
