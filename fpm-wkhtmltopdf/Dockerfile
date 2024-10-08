ARG php_version=8.3
FROM php:8.3-fpm-alpine

# NOTE: This arg must come after FROM
# https://docs.docker.com/engine/reference/builder/#understand-how-arg-and-from-interact
ARG alpine_version=edge

RUN apk add --no-cache \
        bash \
		git \
        fcgi \
		zip \
		file \
		icu-libs \
		# Required by Workflow Component
		graphviz \
        ttf-freefont \
		# Required by Message Component
        rabbitmq-c \
        rabbitmq-c-dev \
		# Required by LiipImagineBundle
		freetype \
		libpng \
        libjpeg-turbo \
        freetype-dev \
        libpng-dev \
        libjpeg-turbo-dev \
        libxml2-dev \
        libzip-dev \
        # Required by soap
        php-soap \
        php-zip \
        supervisor \
        dcron \
        netcat-openbsd

RUN set -eux \
    && apk add --no-cache --virtual .build-deps \
        autoconf \
        dpkg \
        dpkg-dev \
        file \
        g++ \
        gcc \
        libc-dev \
        make \
        pkgconf \
        re2c \
        icu-dev \
    && docker-php-ext-configure gd --enable-gd --with-freetype --with-jpeg \
    && docker-php-ext-install \
        intl \
        pdo_mysql \
        gd \
    ftp \
        soap \
        zip \
    && pecl install \
        amqp-1.11.0 \
        redis \
        excimer \
    && docker-php-ext-enable --ini-name 05-opcache.ini opcache \
    && docker-php-ext-enable amqp \
    && docker-php-ext-enable redis \
    && docker-php-ext-enable ftp \
    && docker-php-ext-enable excimer \
    && apk del .build-deps



COPY --from=surnet/alpine-wkhtmltopdf:3.20.1-0.12.6-small /bin/wkhtmltopdf /bin/

RUN chmod +x /bin/wkhtmltopdf && \
    ln -s /bin/wkhtmltopdf /usr/bin/wkhtmltopdf && \
    rm -rf /tmp/* && \
    rm -rf /var/cache/apk/*
