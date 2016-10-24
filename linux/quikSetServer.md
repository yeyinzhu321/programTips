![alt](http://placeimg.com/600/300/people)
## 5分钟搭建ubuntu服务器环境 
<!--more-->
搭建环境其实很简单，其实根本不用来回百度、google，
用了一次下次就知道了。
### mysql
```
#首先更新apt-get服务(保证最新源)
sudo apt-get update

#安装mysql服务 (会提示你输入passwd)
sudo apt-get install mysql-server 
sudo apt-get install mysql-client 
sudo apt-get install libmysqlclient-dev 

#测试mysql是否正常运行
sudo netstat -tap | grep mysql 

#若配置出现问题打算重新安装
sudo apt-get autoremove –purge mysql-server 
sudo apt-get autoremove –purge mysql-client  
sudo apt-get autoremove –purge libmysqlclient-dev  
sudo apt-get autoremove –purge mysql-common

```

### nginx
```
sudo apt-get install nginx 

#若是想知道安装在哪里？
whereis nginx 

#若想对nginx进行个性化配置？
/etc/nginx/nginx.conf //老司机都不用解释(配置文件)

```
### node
```
#ubuntu下最简单的node和npm安装
#先去官网下载linux版本到本机解压
export NODE_HOME=your location(你解压的位置)
export PATH=PATH:NODE_HOME/bin 
export NODE_PATH=$NODE_HOME/lib/node_modules

#测试
node -v
npm -v

ok,大功告成
```

### 管理你的node.js服务


推荐 pm2
```
现在环境已经搭建成功，只要运行你的 npm app.js  
或者 npm start即可。
但是每当ctrl+c或者 shh登录超时，那么很不幸的告诉你，你的node也挂了。
so...下载一个管理工具吧。

sudo npm install -g pm2
 #如果不能翻墙向你推荐cnpm，不过有条件尽量还是翻墙吧，因为有的集成安装包是默认执行 npm install 下载任务的 
 #比如 你下载了 yo ---- sudo yo jhipster
 #如果你不能翻墙那你就等着煎熬吧，言归正传：

//对于我们掌握几条命令就可以管理

$ pm2 start app.js --name my-api # 命名进程
$ pm2 list               # 显示所有进程状态
$ pm2 monit              # 监视所有进程
$ pm2 logs               #  显示所有进程日志
$ pm2 stop all           # 停止所有进程
$ pm2 restart all        # 重启所有进程
$ pm2 stop 0             # 停止指定的进程
$ pm2 restart 0          # 重启指定的进程
$ pm2 delete all         # 杀死全部进程
 
 ps：还有几条命令根本就用不上，没必要记忆


```
然后做好备份镜像，维护你的服务器吧
