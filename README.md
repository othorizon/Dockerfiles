# Dockerfiles

各类dockerfile配置

镜像官网：https://hub.docker.com/u/itrizon

- [Dockerfiles](#dockerfiles)
  - [git 客户端](#git-客户端)
  - [netease-dl](#netease-dl)
  - [music-get](#music-get)
  - [dzzoffice 安装说明](#dzzoffice-安装说明)
  - [各种docker镜像相关链接](#各种docker镜像相关链接)

## git 客户端

## netease-dl

网易云音乐下载

```bash
docker run --rm -it -v /targetDir:/output itrizon/netease-dl:latest playlist -i id
```

## music-get

云音乐下载

```bash
docker run --rm -it -v /targetDir:/data/downloads itrizon/music-get:latest /data/musci-get $url
```

## dzzoffice 安装说明

[dzzoffice/install.md](/dzzoffice/install.md)

## 各种docker镜像相关链接
