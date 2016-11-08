## php7-fpm-nginx-alpine-composer

This image:

 - starts from php:7.0-fpm-alpine
 - installs composer
 - adds nginx:1.10.2-alpine with its nginx.conf and a modified nginx.vh.default.conf
 - installs and configures supervisord per [docker docs](https://docs.docker.com/engine/admin/using_supervisord/)

#### Example Dockerfile:

```
FROM <imageuri>

# copy your php source code from src folder
COPY src/ /usr/share/nginx/html/

# optional: custom php.ini file
# COPY config/php.ini /usr/local/etc/php/

# optional: install dependencies from composer.json
# WORKDIR /usr/share/nginx/html/
# composer install

# optional: install custom nginx config file
# COPY nginx.site.conf /etc/nginx/conf.d/default.conf

EXPOSE 80 443

CMD ["/usr/bin/supervisord"]
```
