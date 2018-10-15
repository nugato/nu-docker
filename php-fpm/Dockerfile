FROM alpine:3.8

ENV TIMEZONE UTC
ENV MEMORY_LIMIT 2G
ENV MAX_EXECUTION_TIME 0

RUN apk add --update \
    php7-fpm \
    php7-apcu \
    php7-ctype \
    php7-curl \
    php7-dom \
    php7-gd \
    php7-iconv \
    php7-imagick \
    php7-json \
    php7-intl \
    php7-mcrypt \
    php7-mbstring \
    php7-opcache \
    php7-openssl \
    php7-pdo \
    php7-pdo_mysql \
    php7-mysqli \
    php7-xml \
    php7-xmlreader \
    php7-xmlwriter \
    php7-zlib \
    php7-phar \
    php7-tokenizer \
    php7-session \
    php7-simplexml \
    php7-xdebug \
    php7-fileinfo \
    php7-exif \
    php7-zip \
    make \
    curl \
    vim

RUN rm -rf /var/cache/apk/* && rm -rf /tmp/* && \
    curl --insecure https://getcomposer.org/composer.phar -o /usr/bin/composer && chmod +x /usr/bin/composer

ADD php.ini /etc/php7/php-fpm.d/
ADD php.ini /etc/php7/cli/conf.d/
ADD xdebug.ini  /etc/php7/conf.d/

ADD symfony.pool.conf /etc/php7/php-fpm.d/

RUN sed -i "s|;*date.timezone =.*|date.timezone = ${TIMEZONE}|i" /etc/php7/php.ini && \
	sed -i "s|;*memory_limit =.*|memory_limit = ${MEMORY_LIMIT}|i" /etc/php7/php.ini && \
	sed -i "s|;*max_execution_time =.*|max_execution_time = ${MAX_EXECUTION_TIME}|i" /etc/php7/php.ini

CMD ["php-fpm7", "-F"]

WORKDIR /var/www
EXPOSE 9000