FROM busybox as stage1
ENV DZZ_URL https://github.com/zyx0814/dzzoffice/archive/2.02.zip
RUN wget $DZZ_URL
RUN unzip 2.02.zip

FROM php:5.6-apache
RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng-dev \
    && docker-php-ext-install -j$(nproc) mcrypt mysql zip \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd
# 将解压的程序复制到php容器中
COPY --from=stage1 dzzoffice-2.02/ /var/www/html/
EXPOSE 80
# 网盘上传附件目录
VOLUME /var/www/html/data/attachment/dzz
# 赋予权限，如果启动时使用-v映射了目录，那么镜像启动后还需要exec进入后重新授权一次被挂载目录的权限
RUN chown -R www-data:www-data /var/www/html/config /var/www/html/data