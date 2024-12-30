# PHP Docker Images

This repository contains Docker images for PHP applications with different configurations:

## Available Images

### FPM Images

- `mdiakhatenv/nv-php:fpm-8.3-wkhtmltopdf` - PHP 8.3 FPM with wkhtmltopdf
- `mdiakhatenv/nv-php:fpm-8.2-wkhtmltopdf` - PHP 8.2 FPM with wkhtmltopdf 
- `mdiakhatenv/nv-php:fpm-8.1-wkhtmltopdf` - PHP 8.1 FPM with wkhtmltopdf

### CLI Images (Commented out in Makefile)

- `mdiakhatenv/nv-php:cli-8.3` - PHP 8.3 CLI
- `mdiakhatenv/nv-php:cli-8.2` - PHP 8.2 CLI
- `mdiakhatenv/nv-php:cli-8.1` - PHP 8.1 CLI

### CLI with Composer Images (Commented out in Makefile)

- `mdiakhatenv/nv-php:cli-8.3-composer` - PHP 8.3 CLI with Composer
- `mdiakhatenv/nv-php:cli-8.2-composer` - PHP 8.2 CLI with Composer
- `mdiakhatenv/nv-php:cli-8.1-composer` - PHP 8.1 CLI with Composer

## Features

All images include:

- PHP extensions:
  - intl
  - pdo_mysql
  - gd
  - ftp
  - soap
  - zip
  - amqp
  - redis
  - excimer
  - opcache

- Additional packages:
  - git
  - zip
  - icu-libs
  - graphviz
  - rabbitmq-c
  - freetype
  - libpng
  - supervisor
  - dcron
  - wkhtmltopdf

## Building Images

The repository includes a Makefile to simplify building the Docker images:

### Configuration Variables

- `REPO=mdiakhatenv/nv-php` - Base repository name for images
- `VERSIONS="8.1 8.2 8.3"` - PHP versions to build
- `COMPOSER_VERSION=2.7.7` - Composer version for CLI images
- `BUILDKIT_PROGRESS=plain` - BuildKit progress output format

### Available Make Targets

- `make build` - Builds all images (currently configured for FPM images with wkhtmltopdf)
- `make cli` - Builds CLI images (currently commented out)
- `make fpm` - Builds FPM images (currently commented out)
- `make cli-8.3` - Builds PHP 8.3 CLI image specifically

### Building Specific Versions

To build a specific version:

