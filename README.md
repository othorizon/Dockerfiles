# Dockerfiles

各类dockerfile配置

镜像官网：https://hub.docker.com/u/itrizon

- [Dockerfiles](#dockerfiles)
  - [git 客户端](#git-客户端)
  - [网易云音乐下载](#网易云音乐下载)
  - [dzzoffice 安装说明](#dzzoffice-安装说明)
  - [各种docker镜像相关链接](#各种docker镜像相关链接)

## git 客户端

## 网易云音乐下载

```bash
docker pull itrizon/netease-dl:latest
docker run --rm -it -v /targetDir:/output netease-dl:latest playlist -i id
```

## dzzoffice 安装说明

[dzzoffice/install.md](/dzzoffice/install.md)

## 各种docker镜像相关链接
