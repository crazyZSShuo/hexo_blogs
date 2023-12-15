### 使用公钥

wget -qO - https://www.mongodb.org/static/pgp/server-5.0.asc | sudo apt-key add -

### 创建mongodb列表文件

mkdir /etc/apt/sources.list.d/mongodb-org-5.0.list

### 查看当前系统版本

lsb_release -dc

### 注册mongo源

echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/5.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-5.0.list

### 更新源

sudo apt-get update

### 开始安装

sudo apt-get install -y mongodb-org=5.0.6 mongodb-org-server=5.0.6 mongodb-org-shell=5.0.6 mongodb-org-mongos=5.0.6 mongodb-org-tools=5.0.6

### 创建数据存储目录

sudo mkdir -p /opt/database/mongodb/data/db

### 查看配置文件

vim /etc/mongod.conf

### 更改数据库目录路径

storage:
  #dbPath: /var/lib/mongodb
  dbPath: /opt/database/mongodb/data/db

### 修改目录权限，该文件只属于mongodb用户组

cd /opt/database/ && sudo chown -R mongodb:mongodb mongodb/


### 管理mongo服务 

sudo systemctl daemon-reload

sudo systemctl restart mongod.service

sudo systemctl start/status mongod.service



