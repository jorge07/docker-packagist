FROM jorge07/alpine-php:7-dev

ENV SYMFONY_ENV prod

ADD https://github.com/composer/packagist/archive/master.tar.gz /tmp

RUN mkdir /tmp_pr && tar zxvf /tmp/master.tar.gz -C /tmp_pr && mv /tmp_pr/packagist-master/* /app && rm -rf /tmp_pr

COPY parameters.yml.dist /app/app/config/parameters.yml

RUN composer install --no-ansi --no-dev --no-interaction --no-progress --optimize-autoloader \
    && php app/console c:w && app/console a:i web

COPY config/crontab /var/spool/cron/crontabs/packagist
COPY config/supervisor/supervisor.conf /etc/supervisor/conf.d/supervisord.conf

EXPOSE 9000

VOLUME /app/web
