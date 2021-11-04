FROM centos:centos7

RUN yum -y update

# リポジトリ epel, remi
RUN yum -y install epel-release
RUN yum install -y https://rpms.remirepo.net/enterprise/remi-release-7.rpm

# apatch, phpをインストール
RUN yum -y install httpd
RUN yum -y install php80 php80-php php80-php-fpm php80-php-bcmath php80-php-json php80-php-mbstring php80-php-pdo php80-php-xml php80-php-mysqlnd php80-php-redis --enablerepo=remi-php80 composer && \
ln -sf /usr/bin/php80 /usr/bin/php
RUN yum -y install zip unzip git

RUN php80 -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" 
RUN php80 composer-setup.php --install-dir=/usr/bin --filename=composer 

COPY my-php.ini /etc/opt/remi/php80/php.ini

ENTRYPOINT ["/usr/sbin/httpd", "-D", "FOREGROUND"]

WORKDIR /var/www/html