FROM 024789436172.dkr.ecr.us-east-2.amazonaws.com/base/laravel_mysql_composer:latest
CMD pwd
CMD ls
COPY jobs/laravel/deploy/000-default.conf /etc/apache2/sites-available/000-default.conf
COPY jobs/laravel/deploy/.env-pro /var/www/html/.env

# Suppress the do-not-run-as-root warning from composer
ENV COMPOSER_ALLOW_SUPERUSER 1

COPY . /var/www/html/
WORKDIR /var/www/html/

RUN chown -R www-data:wwwdata /var/www/html \
    && composer install
    #&& php artisan key:generate
#CMD service apache2 start