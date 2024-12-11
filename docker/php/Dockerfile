FROM php:8.3-fpm

WORKDIR /var/www

# Limpeza de diretório desnecessário
RUN rm -rf /var/www/html

# Instalação de dependências
RUN apt-get update && apt-get install -y \
    build-essential \
    libpng-dev \
    libjpeg62-turbo-dev \
    libfreetype6-dev \
    locales \
    zip \
    jpegoptim optipng pngquant gifsicle \
    vim \
    unzip \
    git \
    curl \
    libzip-dev \
    apt-utils \
    libonig-dev && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

# Instalação de extensões PHP
RUN docker-php-ext-install zip pdo_mysql mbstring exif
RUN docker-php-ext-configure gd --with-freetype=/usr/include/ --with-jpeg=/usr/include/
RUN docker-php-ext-install gd

# Instalação do Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Configuração do usuário Laravel
RUN groupadd -g 1000 laravel && \
    useradd -u 1000 -ms /bin/bash -g laravel user

COPY --chown=user:laravel . /var/www

USER user

EXPOSE 9000

CMD ["php-fpm"]