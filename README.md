# Dockerfiles

各类dockerfile配置

镜像官网：https://hub.docker.com/u/itrizon

## git 客户端

## 网易云音乐下载

```bash
docker pull itrizon/netease-dl:latest
docker run --rm -it -v /targetDir:/output netease-dl:latest playlist -i id
```

## 各种docker镜像相关链接
