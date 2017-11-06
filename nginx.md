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
