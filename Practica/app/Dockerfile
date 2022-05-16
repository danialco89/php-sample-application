FROM php:7.4-apache
ENV DEBIAN_FRONTEND=noninteractive
RUN apt update -y && apt install wget unzip -y
COPY php-sample-application /opt/php-sample-application/
COPY Sample.conf /etc/apache2/sites-enabled/
#RUN apt install wget unzip -y
WORKDIR /opt/php-sample-application
RUN make
RUN a2enmod rewrite
RUN docker-php-ext-install pdo pdo_mysql
RUN service apache2 restart
RUN chgrp www-data /opt/php-sample-application -R
RUN chmod g+w /opt/php-sample-application -R
#CMD ["apache2-foreground"]
