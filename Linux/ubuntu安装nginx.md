本文将会介绍怎么在 Ubuntu 上安装 nginx 服务，这里使用的方法是 Nginx 官方提供的，在此记录下来以便下次方便查阅。



## Install the prerequisites:

`sudo apt install curl gnupg2 ca-certificates lsb-release`

## To set up the apt repository for stable nginx packages, run the following command:

```bash
echo "deb http://nginx.org/packages/ubuntu `lsb_release -cs` nginx" \
    | sudo tee /etc/apt/sources.list.d/nginx.list
```

## Next, import an official nginx signing key so apt could verify the packages authenticity:

```bash
curl -fsSL https://nginx.org/keys/nginx_signing.key | sudo apt-key add -
```

## Verify that you now have the proper key:

```bash
sudo apt-key fingerprint ABF5BD827BD9BF62
```

## The output should contain the full fingerprint 573B FD6B 3D8F BC64 1079 A6AB ABF5 BD82 7BD9 BF62 as follows:

```
pub   rsa2048 2011-08-19 [SC] [expires: 2024-06-14]
      573B FD6B 3D8F BC64 1079  A6AB ABF5 BD82 7BD9 BF62
uid   [ unknown] nginx signing key <signing-key@nginx.com>
```

## To install nginx, run the following commands:

```shell
sudo apt update
sudo apt install nginx
```



## Nginx 官网相关链接

1. 下载地址 [https://nginx.org/en/download.html](https://nginx.org/en/download.html)
2. 官方文档 [https://nginx.org/en/docs/](https://nginx.org/en/docs/)

