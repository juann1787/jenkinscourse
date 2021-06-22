FROM php:7.2-apache
LABEL maintainer="Jaivic"

RUN a2enmod rewrite

RUN apt-get update && apt-get install -y \
        zlib1g-dev \
        libicu-dev \
        libxml2-dev \
        libpq-dev\
        vim \
        #&& docker-php-ext-configure pgsql -with-pgsql=/usr/local/pgsql \
        && docker-php-ext-install pdo pdo_mysql zip intl xmlrpc soap opcache \
        && docker-php-ext-configure pdo_mysql --with-pdo-mysql=mysqlnd
       # && apt-get install vim -y
# Add Node 8 LTS
RUN curl -sL https://deb.nodesource.com/setup_8.x | bash -- \
        && apt-get install -y nodejs \
        && apt-get autoremove -y

# Update NPM to the last version
# RUN npm install -g npm@latest \
#       && rm -r /.npm

# Add Composer
COPY --from=composer /usr/bin/composer /usr/bin/composer

