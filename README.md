# composer-apache-base
Base image for building and running php web apps

Usage:

use this image as a base image for your php application

```
FROM ackee/composer-apache-base

# install app
WORKDIR /var/www/
COPY . /var/www/
RUN chown -R www-data:www-data /var/www/ && \
    su -s /bin/bash www-data -c '\
       composer install && \
       rm -rf /var/www/html/ && \
       ln -s /var/www/www/ /var/www/html && \
       rm -rf /var/www/temp && \
       ln -s /var/app-persistent-storage/temp /var/www/temp && \
       ln -s /var/app-persistent-storage/log /var/www/log && \
       ln -s /var/app-persistent-storage/uploads /var/www/html/uploads && \
       ln -s ../log/ /var/www/www/log '
```
