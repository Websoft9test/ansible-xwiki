# Xwiki.Notes

组件名称：xwiki
安装文档：https://www.xwiki.org/xwiki/bin/view/Documentation/AdminGuide/Installation/
配置文档：https://www.xwiki.org/xwiki/bin/view/Documentation/AdminGuide/Configuration/
支持平台：Debian家族 | RHEL家族 | Windows | macOS | Docker

责任人：helin

## 概要

XWiki是使用[Java](https://baike.baidu.com/item/Java/85979)编写的[开源](https://baike.baidu.com/item/开源/20720669)[Wiki](https://baike.baidu.com/item/Wiki/97755)引擎，它的开发平台特性允许创建协作式[Web](https://baike.baidu.com/item/Web/150564)应用，同时也提供了构建于平台之上的[打包](https://baike.baidu.com/item/打包/23389687)应用（第二代Wiki)。

## 环境要求

* 程序语言： java
* 应用服务器：自选
* 数据库:   自选
* 依赖组件：java
* 其他：

## 安装说明

下面基于不同的安装平台，分别进行安装说明。

### 

```shell
###on CentOS

yum install java     -y   #安装java
yum install unzip -y #安装unzip 
###on Ubuntu         
apt-get update          
apt install java        
apt install unzip -y  #安装unzip 

wget http://nexus.xwiki.org/nexus/content/groups/public/org/xwiki/platform/xwiki-platform-distribution-jetty-hsqldb/12.3/xwiki-platform-distribution-jetty-hsqldb-12.3.zip  /usr/local
cd /usr/local/xwiki-platform-distribution-jetty-hsqldb-12.3
./start_xwiki.sh

 

---
- hosts: 172.28.2.89   #zhujiqingdan
  remote_user: root
  tasks:
  - name: fenfawenjian
    copy:
     src: '{{ item.src }}'
     dest: /home/smk/
     owner: root
     group: root
     mode: 0755
    with_items:
    - { src: '/home/smk/hel.sh' }
  - name: doshell
    command: sleep 3
  - name: doshell2
    shell: /bin/bash /home/smk/hel.sh
 


```





## 路径

* 程序路径：     /usr/local/
* 日志路径： **/var/lib/xwiki/data**
* 配置文件路径：/usr/local/xwiki-platform-distribution-jetty-hsqldb-12.3/webapps/xwiki/WEB-INF/xwiki.cfg
* 启动路径:       /usr/local/
* 其他...

## 配置

安装完成后，需要依次完成如下配置



```shell
vi /usr/local/xwiki-platform-distribution-jetty-hsqldb-12.3/webapps/xwiki/WEB-INF/xwiki.cfg
 xwiki.superadminpassword=您的密码  
systemctl restart xwiki         #修改超级管理员账户  


```

## 账号密码

### 数据库密码

如果有数据库

* 数据库安装方式：
* 账号密码：

### 后台账号

如果有后台账号

* 登录地址  http://服务器IP:8080

* 账号密码: 在web管理界面自行创建

  如果启动了超级管理员账户：账户为 superadmin 密码为您设置的密码

* 密码修改方案：

  vi /usr/local/xwiki-platform-distribution-jetty-hsqldb-12.3/webapps/xwiki/WEB-INF/xwiki.cfg
   xwiki.superadminpassword=您的密码


## 服务

本项目安装后无服务,需自行编写服务

服务文件位置：/etc/systemd/system/xwiki.service

```
[Unit]
Description=xwiki
After=network.target

[Service]
Type=simple

Environment="XWIKI_HOME=/usr/local/xwiki-platform-distribution-jetty-hsqldb-12.3"
ExecStart=/usr/local/xwiki-platform-distribution-jetty-hsqldb-12.3/start_xwiki.sh
ExecStop=/usr/local/xwiki-platform-distribution-jetty-hsqldb-12.3/stop_xwiki.sh

[Install]
WantedBy=multi-user.target
                    
                    
```

## 环境变量

列出需要增加的环境变量以及增加环境变量的命令：

* 名称 | 路径

## 版本号

通过如下的命令获取主要组件的版本号: 

```
# Check xwiki version
cat /usr/local/xwiki-platform-distribution-jetty-hsqldb-12.3/webapps/xwiki/WEB-INF/version.properties
```

## 常见问题

#### 有没有管理控制台？

*http:// 公网 IP:8080

#### 本项目需要开启哪些端口？

| item         | port |
| ------------ | ---- |
| 管理平台端口 | 8080 |
|              |      |
|              |      |

#### 有没有CLI工具？

无

## 日志

* 2020-05-20完成安装研究

