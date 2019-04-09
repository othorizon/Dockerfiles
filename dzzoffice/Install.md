# dzzoffice docker版安装说明

参考：[Docker环境中部署DzzOffice 1.2.5.2](https://www.cnblogs.com/jytx/p/5443181.html)

```dockerfile
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
COPY dzzoffice-2.02/ /var/www/html/
# 网盘附件目录
VOLUME /var/www/html/data/attachment/dzz
# 赋予权限，如果把目录使用-v映射到镜像外面，那么镜像启动后还需要重新授权一次被挂载目录的权限
RUN chown -R www-data:www-data /var/www/html/config /var/www/html/data
```

## 安装onlyoffice

`docker run --name onlyoffice -itd -p 9011:80 dzzoffice/onlyoffice`
dzz中的onlyoffice配置路径:`http://[可访问的外部ip]:9011/web-apps/apps/api/documents/api.js`