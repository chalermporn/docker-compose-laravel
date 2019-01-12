#php ใช้ version 7.1 สามารถเปลี่ยนได้ตามที่เราต้องการแต่ต้องเป็นตัว fpm นะครับ เพื่อที่จะให้กับ nginx
FROM php:7.1-fpm

#Install คำสั่งสำหรับการลง package ที่ laravel required ไว้นะครับ
RUN apt-get update \
  && apt-get install -y \
    cron \
    libfreetype6-dev \
    libicu-dev \
    libjpeg62-turbo-dev \
    libmcrypt-dev \
    libpng-dev \
    libxslt1-dev \
    openssh-server \
    openssh-client \
    rsync

RUN docker-php-ext-configure \
  gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/

# ตามด้วยคำสั่งสำหรับการลง php extension ครับ
RUN docker-php-ext-install \
  bcmath \
  gd \
  intl \
  mbstring \
  mcrypt \
  pdo_mysql \
  soap \
  xsl \
  zip

# อันนี้ลงเพิ่มเติมคือ composer นั้นเอง เป็นตัว package manager สำหรับการจัดการพวก dependency ของภาษา php ครับ
RUN curl -sS https://getcomposer.org/installer | \
  php -- --install-dir=/usr/local/bin --filename=composer
