---
title: nginx
date: 2022-07-07 10:24:06
updated: 2022-07-07 19:24:06
tags:
  - java
  - 服务器
  - nginx
category:
  - java
  - 服务器
---

## http

[2万字 让你全面认识 Nginx，收藏 ！](https://zhuanlan.zhihu.com/p/369926646)

[超详细的Nginx负载均衡+高可用配置](https://blog.csdn.net/IT_10/article/details/89365436)

[史上讲解最好的Nginx 教程，从入门到精通](https://zhuanlan.zhihu.com/p/389438482)

### location

**路径映射：**

- 精确匹配
- 前缀匹配
- 正则匹配

```shell
#    rewrite /yang/(.*) /$1;
-----------------------------------
location /yang {
    proxy_pass  http://node/;
    #proxy_set_header    Host    $http_host;
    #proxy_set_header    X-Real-IP   $remote_addr;
    #proxy_set_header    X-Forwarded-For $proxy_add_x_forwarded_for;
    #root   /usr/share/nginx/html;
    #index  index.html index.htm;ß
}

------------------------------------
server {
    listen 8081;
    server_name localhost;
    location /yang/ {
        alias /home/yang/e1/;# 访问http://101.200.208.190/yang/index3.html，实际在服务器找的路径		是/home/yang/e1/index3.html
        index  index.html index.htm;
    }
}
server {
    listen 8082;
    server_name localhost;
    location /yang {
        alias /home/yang/e2/;# 访问http://101.200.208.190/yang/index3.html，实际在服务器找的路径是/home/yang/e1//index3.html
        index  index.html index.htm;
    }
}
server {
    listen 8083;
    server_name localhost;
    location /yang {
        alias /home/yang/e3/;
        index  index.html index.htm;
    }
}
upstream node {
    server localhost:8081;
    server localhost:8082;
    server localhost:8083;
}
```

