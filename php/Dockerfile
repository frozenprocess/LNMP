FROM centos:7

RUN yum update -y

RUN yum install epel-release https://rpms.remirepo.net/enterprise/remi-release-7.rpm -y

RUN yum install --enablerepo=remi-php74 php php-fpm php-mbstring php-pdo php-xml php-zip php-redis php-mysql php-xdebug unzip git -y

RUN curl https://getcomposer.org/download/1.9.1/composer.phar > /sbin/composer && chmod +x /sbin/composer

COPY www.conf /etc/php-fpm.d/www.conf

RUN mkdir /run/php-fpm

RUN mkdir -p /var/www

WORKDIR /var/www

RUN echo $'[xdebug] \n\
xdebug.remote_enable=1 \n\
xdebug.remote_port="9000" \n\
xdebug.idekey="stphp"' >> /etc/php.ini

EXPOSE 8000/tcp
EXPOSE 9000/tcp

CMD [ "php-fpm","-F","-R" ]