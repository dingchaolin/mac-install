## 安装
- brew install nginx

## 配置文件路径
- /usr/local/etc/nginx

### nignx 测试配置文件
- sudo nginx -t

### 重新加载配置文件
- sudo nginx -s reload

### 错误
- nginx: [error] invalid PID number “” in “/usr/local/var/run/nginx/nginx.pid”
- sudo nginx -c /usr/local/etc/nginx/nginx.conf
- sudo nginx -s reload


## centos 配置
- 添加一个配置信息
```
#server
       server {
           listen       80;
           server_name  verifycode.artron.net;
           access_log  logs/captcha_access.log  main;
     
           location / {
                proxy_pass http://127.0.0.1:30005;
     
                proxy_set_header Upgrade $http_upgrade;
                proxy_set_header Connection "upgrade";
                proxy_http_version 1.1;
                proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
                proxy_set_header Host $host;
                proxy_set_header X-Real-IP $remote_addr;
           }
      }

```
- 启动
- cd sbin 
- sudo ./nginx -c ./conf/nginx.conf
- cd /
- ./data/nginx/sbin/nginx -s reload