# mac-install

###  安装homebrew
- /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

### 更新homebrew
- brew update

### 安装node
- brew install node

### 安装pm2
- brew install pm2 -g

### 安装 typescript
- brew install typescript

### 安装 n
- brew install n

### 安装typings
- npm install typings -g

### 修改hosts
- cd /
- sudo vi private/etc/hosts

### 安装redis
- brew install redis

### 启动redis
- redis-server

### 启动redis客户端
- redis-cli


### 安装mysql
- brew install mysql

### 查看mysql安装信息
- brew info mysql

### 启动mysql
- brew services start mysql
- mysql.server start

### 重启mysql
- brew services restart mysql

## 连接mysql
- mysql -u root

## 使用账号密码连接
- mysql -u root -p

## 退出连接
- exit;

## 查看所有数据库
- show databases;

## 选择一个数据库
- use mysql；

## 查看所有的数据库表
- show tables;


