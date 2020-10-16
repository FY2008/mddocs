首先 Nginx 默认的配置文件通常为 nginx.conf，路径一般在 `/usr/local/nginx/conf, /etc/nginx, /usr/local/etc/nginx`



我实际在 `Ubuntu` 下用 apt 安装的 nginx 的配置文件在 `/etc/nginx` 下

## /etc/nginx 树结构

```shell
zsfxx@DESKTOP-N95R1I7:/etc/nginx$ tree
.
├── conf.d
│   └── default.conf
├── fastcgi_params
├── koi-utf
├── koi-win
├── mime.types
├── modules -> /usr/lib/nginx/modules
├── nginx.conf
├── scgi_params
├── uwsgi_params
└── win-utf

2 directories, 9 files
```



下面列出 `nginx` 几个默认的配置文件

## nginx.conf

```nginx
# /etc/nginx/nginx.conf
user  nginx;
worker_processes  1;

error_log  /var/log/nginx/error.log warn;
pid        /var/run/nginx.pid;


events {
    worker_connections  1024;
}


http {
    include       /etc/nginx/mime.types;
    default_type  application/octet-stream;

    log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
                      '$status $body_bytes_sent "$http_referer" '
                      '"$http_user_agent" "$http_x_forwarded_for"';

    access_log  /var/log/nginx/access.log  main;

    sendfile        on;
    #tcp_nopush     on;

    keepalive_timeout  65;

    #gzip  on;

    include /etc/nginx/conf.d/*.conf; # 这里包含了 conf.d目录下的所有配置文件
}
```

## default.conf

```nginx
server {
    listen       80;
    server_name  localhost;

    #charset koi8-r;
    #access_log  /var/log/nginx/host.access.log  main;

    location / {
        root   /usr/share/nginx/html;
        index  index.html index.htm;
    }

    #error_page  404              /404.html;

    # redirect server error pages to the static page /50x.html
    #
    error_page   500 502 503 504  /50x.html;
    location = /50x.html {
        root   /usr/share/nginx/html;
    }

    # proxy the PHP scripts to Apache listening on 127.0.0.1:80
    #
    #location ~ \.php$ {
    #    proxy_pass   http://127.0.0.1;
    #}

    # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
    #
    #location ~ \.php$ {
    #    root           html;
    #    fastcgi_pass   127.0.0.1:9000;
    #    fastcgi_index  index.php;
    #    fastcgi_param  SCRIPT_FILENAME  /scripts$fastcgi_script_name;
    #    include        fastcgi_params;
    #}

    # deny access to .htaccess files, if Apache's document root
    # concurs with nginx's one
    #
    #location ~ /\.ht {
    #    deny  all;
    #}
}
```





我们经常会忘记一个命令的用法，nginx 作为经常使用的命令，所以要把常用的命令记录下来方便忘记时查找。

* nginx -s reload
* nginx -s  stop
* nginx -s reopen
* nginx
* nginx -t 测试配置文件