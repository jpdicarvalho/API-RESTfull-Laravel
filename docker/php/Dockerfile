FROM php:8.2-fpm

# Instalar extensões do PHP e dependências necessárias
RUN apt-get update && apt-get install -y \
    git \
    curl \
    libpng-dev \
    libonig-dev \
    libxml2-dev \
    zip \
    unzip \
    && docker-php-ext-install pdo_mysql mbstring exif pcntl bcmath gd

# Instalar Composer
COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

# Definir diretório de trabalho
WORKDIR /var/www

# Configurar permissões
RUN chown -R www-data:www-data /var/www

# Expor a porta para o Laravel
EXPOSE 9000