FROM php:8.1-fpm

RUN apt-get update && apt-get install -y     git curl zip unzip libpq-dev libonig-dev libxml2-dev     && docker-php-ext-install pdo pdo_mysql mbstring exif pcntl bcmath gd

COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

WORKDIR /var/www/html

COPY . .

RUN composer install --no-dev --optimize-autoloader     && cp .env.example .env     && php artisan key:generate

CMD ["php-fpm"]
