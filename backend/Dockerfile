FROM php:8.2-apache

# Instala extensões necessárias
RUN apt-get update && apt-get install -y \
    git unzip curl libpq-dev \
    && docker-php-ext-install pdo pdo_pgsql

# Ativa o mod_rewrite (importante pro Laravel)
RUN a2enmod rewrite
RUN a2ensite 000-default.conf

# Instala o Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Define diretório do projeto
WORKDIR /var/www/html

# Copia os arquivos
COPY . .

# Permissões para storage e cache
RUN chown -R www-data:www-data storage bootstrap/cache