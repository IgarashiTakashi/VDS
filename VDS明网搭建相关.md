#### 用户相关

linux下 useradd liyu

#### java相关

##### Ubuntu 16.04 安装jdk

1. 准备工作

- 安装版本：jdk-8u91-linux-x64.tar.gz
- [官方下载](https://link.jianshu.com?t=http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)

------

1. 创建目录作为JDK的安装目录，这里选择安装位置为:/usr/java/

```
sudo mkdir /usr/java
```

------

1. 解压文件带/usr/java/目录下，cd到文件下载的位置

```
sudo tar zxvf jdk-8u90-linux-x64.tar.gz -C /usr/java/
```

------

1. 改名jdk-8u90-linux-x64为jdk，便于配置环境变量

```
sudo mv jdk-8u90-linux-x64 jdk
```

------

1. 配置系统环境变量
    打开环境变量文件

```
sudo gedit /etc/environment
```

填写内容，注意加粗部分

```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:$JAVA_HOME/bin"

export CLASSPATH=.:$JAVA_HOME/lib:$JAVA_HOME/jre/lib

export JAVA_HOME=/usr/java/jdk

export JRE_HOME=${JAVA_HOME}/jre  
```

------

1. 配置所有用户环境变量
    打开用户环境变量配置文件

```
sudo gedit /etc/profile
```

填写内容

```
#set Java environment

JAVA_HOME=/usr/java/jdk

export JRE_HOME=/usr/java/jdk/jre

export CLASSPATH=.:$JAVA_HOME/lib:$JRE_HOME/lib:$CLASSPATH

export PATH=$JAVA_HOME/bin:$JRE_HOME/bin:$PATH
```

------

1. 设置默认jdk

```
sudo update-alternatives --install "/usr/bin/java" "java" "/usr/java/jdk/bin/java" 300

sudo update-alternatives --install "/usr/bin/javac" "javac" "/usr/java/jdk/bin/javac" 300

sudo update-alternatives --install "/usr/bin/javaws" "javaws" "/usr/java/jdk/bin/javaws" 300
```

------

1. 检验安装成功

```
java -version
```

显示结果

```
java version "1.8.0_91"

Java(TM) SE Runtime Environment (build 1.8.0_91-b14)

Java HotSpot(TM) 64-Bit Server VM (build 25.91-b14, mixed mode)
```

##### 安装tomcat

下载安装tomcat（http://tomcat.apache.org/）我这边是下载的apache-tomcat-8.0.50.tar.gz

```
tar -zxvf apache-tomcat-8.0.50.tar.gz
mkdir /usr/local/tomcat
mv apache-tomcat-8.0.50 /usr/local/tomcat/

cd usr/local/tomcat/apache-tomcat-8.0.50/bin/
./startup.sh

成功启动后浏览器输入http://localhost:8080/查看信息（如果不是本机则输入对应IP）
```

#### ubuntu16.04安装Mysql

```
sudo apt-get update
sudo apt-get install mysql-server mysql-client

sudo netstat -tap | grep mysql

sudo vi /etc/mysql/mysql.conf.d/mysqld.cnf
注释掉bind-address = 127.0.0.1：
mysql -uroot -p
grant all on *.* to root@'%' identified by '你的密码' with grant option;
flush privileges;

service mysql restart
```

#### ubuntu 16.04安装redis

```
sudo apt-get install redis-server
 redis-server
```

#### 官网步骤

##### update database

- login mysql(mysql -uroot -p)
- use dimension;
- source dimension.sql

##### clean redis cache

redis-cli keys "source*" | xargs redis-cli del

##### start web service

java -jar vds-1.0.1.jar

密钥：buzz beach fuel thank border flight sweet approve fee sudden shed fence

