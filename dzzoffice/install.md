# dzzoffice docker版安装说明

参考：[Docker环境中部署DzzOffice 1.2.5.2](https://www.cnblogs.com/jytx/p/5443181.html)

使用 [dzzoffice/Dockerfile](/dzzoffice/Dockerfile) 或者自己构建镜像

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

EXPOSE 80
# 将解压的程序复制到php容器中
COPY dzzoffice-2.02/ /var/www/html/
# 网盘附件目录
VOLUME /var/www/html/data/attachment/dzz
# 赋予权限，如果启动时使用-v映射了目录，那么镜像启动后还需要exec进入后重新授权一次被挂载目录的权限
RUN chown -R www-data:www-data /var/www/html/config /var/www/html/data
```

## 安装mysql

`docker run --name mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=root -d mysql:5.7`

## 启动dzzoffice

`docker run --name dzzoffice --link mysql:mysql -d -p 8080:80 -v /workspacec/dzz/dzz_data/:/var/www/html/data/attachment/dzz dzzoffice`

## 安装onlyoffice

dzzoffice支持多种office文档预览的配置，这里以使用onlyoffice为例  

启动onlyoffice服务  
`docker run --name onlyoffice -itd -p 9011:80 dzzoffice/onlyoffice`  

dzz中在应用商店按住onlyoffce，然后配置serverUrl:`http://[可访问的外部ip]:9011/web-apps/apps/api/documents/api.js`  