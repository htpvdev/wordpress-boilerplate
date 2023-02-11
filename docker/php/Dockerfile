FROM php:8.0-apache-buster
SHELL ["/bin/bash", "-oeux", "pipefail", "-c"]

# timezone environment
ENV TZ=UTC \
  # locale
  LANG=ja_JP.UTF-8 \
  LANGUAGE=ja_JP:ja \
  # composer environment
  COMPOSER_ALLOW_SUPERUSER=1 \
  COMPOSER_HOME=/composer

# composer command
COPY --from=composer:2.0 /usr/bin/composer /usr/bin/composer

RUN apt-get update && \
  apt-get -y install libicu-dev libonig-dev libzip-dev unzip locales && \
  apt-get clean && \
  rm -rf /var/lib/apt/lists/* && \
  locale-gen ja_JP.UTF-8 && \
  localedef -f UTF-8 -i ja_JP ja_JP.UTF-8 && \
  a2enmod rewrite && \
  pecl install xdebug-3.1.0 && \
  docker-php-ext-enable xdebug && \
  docker-php-ext-install intl pdo_mysql zip bcmath && \
  composer config -g process-timeout 3600 && \
  composer config -g repos.packagist composer https://packagist.org

COPY ./docker/php/php.ini /usr/local/etc/php/php.ini
# COPY ./infra/php/xdebug.ini /usr/local/etc/php/conf.d/xdebug.ini
COPY ./docker/apache/httpd.conf /etc/apache2/sites-available/000-default.conf

WORKDIR /work/src
