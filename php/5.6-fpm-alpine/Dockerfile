FROM php:5.6-fpm-alpine

RUN apk update && apk add --no-cache \
coreutils \
binutils \
libpng \
libpng-dev \
freetype \
freetype-dev \
libjpeg-turbo \
libjpeg-turbo-dev \
&& docker-php-ext-configure gd \
--with-freetype-dir=/usr/include \
--with-jpeg-dir=/usr/include \
--with-png-dir=/usr/include \
&& docker-php-ext-install -j$(nproc) gd \
&& docker-php-ext-install mysql \
mysqli \
pdo_mysql \
&& apk del --no-cache \
coreutils \
binutils \
libpng-dev \
freetype-dev \
libjpeg-turbo-dev

EXPOSE 9000
CMD ["php-fpm"]