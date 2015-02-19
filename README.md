# ToughRADIUS  [![Build Status](https://travis-ci.org/talkincode/ToughRADIUS.svg?branch=master)](https://travis-ci.org/talkincode/ToughRADIUS)

ToughRADIUS是一个开源的Radius服务软件，基于BSD许可协议发布。

ToughRADIUS支持标准RADIUS协议，提供完整的AAA实现。支持灵活的策略管理，支持各种主流接入设备并轻松扩展，具备丰富的计费策略支持。

ToughRADIUS支持使用Oracle, MySQL, PostgreSQL, MSSQL等主流数据库存储用户数据，并支持数据缓存，极大的提高了性能。
ToughRADIUS支持Windows，Linux，BSD跨平台部署，部署使用简单。

ToughRADIUS提供了RADIUS核心服务引擎与Web管理控制台,用户自助服务三个子系统，核心服务引擎提供高性能的认证计费服务，Web管理控制台提供了界面友好，功能完善的管理功能。用户自助服务系统提供了一个面向终端用户的网上服务渠道。

[ToughRADIUS网站：http://www.toughradius.net] (http://www.toughradius.net)

[ToughRADIUS文档: http://docs.toughradius.net/build/html/] (http://docs.toughradius.net/build/html/)

## Linux下使用脚本在线安装

请保证你的Linux服务器处于联网状态

下载脚本::

    $ curl https://raw.githubusercontent.com/talkincode/ToughRADIUS/master/bin/installer > installer

    $ chmod +x installer

执行安装脚本，根据终端提示进行交互::

    $ ./installer
    
选择你的操作系统类型,默认为centos,注意不同的OS类型的流程提示不一样::

    [INPUT] - select your os type : 1:centos,2:ubuntu,3:freebsd [1]1
    [INFO] - >> Installation Information
    [INFO] - >> installdir: /usr/local/toughradius
    [INFO] - >> rundir: /var/toughradius
    [INFO] - >> log_dir: /var/toughradius/log
    [INFO] - >> mysql_rundir: /var/toughradius/mysql
    [INFO] - >> my_cnf_path: /var/toughradius/mysql/my.cnf
    [INFO] - >> start install centos depend
    [INFO] - >> run command : yum update -y
    [SUCC] - >> run command : yum update -y success!
    [INFO] - >> run command : yum install -y wget git gcc tcpdump crontabs
    [SUCC] - >> run command : yum install -y wget git gcc tcpdump crontabs success!
    [INFO] - >> run command : yum install -y mariadb-devel mysql-devel
    [SUCC] - >> run command : yum install -y mariadb-devel mysql-devel success!
    [INFO] - >> run command : yum install -y python-devel python-setuptools MySQL-python
    [SUCC] - >> run command : yum install -y python-devel python-setuptools MySQL-python success!
    [INFO] - >> run command : easy_install pip
    [SUCC] - >> run command : easy_install pip success!
    [INFO] - >> run command : pip install supervisor
    [SUCC] - >> run command : pip install supervisor success!
    [INFO] - >> run command : pip install argparse
    [SUCC] - >> run command : pip install argparse success!
    [INFO] - >> run command : pip install pycrypto>=2.6.1
    [SUCC] - >> run command : pip install pycrypto>=2.6.1 success!
    [INFO] - >> run command : pip install zope.interface>=4.1.1
    [SUCC] - >> run command : pip install zope.interface>=4.1.1 success!
    [INFO] - >> run command : pip install Twisted>=14.0.2
    [SUCC] - >> run command : pip install Twisted>=14.0.2 success!
    [INFO] - >> run command : pip install autobahn>=0.9.3-3
    [SUCC] - >> run command : pip install autobahn>=0.9.3-3 success!
    [INFO] - >> run command : pip install SQLAlchemy>=0.9.8
    [SUCC] - >> run command : pip install SQLAlchemy>=0.9.8 success!
    [INFO] - >> run command : pip install DBUtils>=1.1
    [SUCC] - >> run command : pip install DBUtils>=1.1 success!
    [INFO] - >> run command : pip install Mako>=0.9.0
    [SUCC] - >> run command : pip install Mako>=0.9.0 success!
    [INFO] - >> run command : pip install Beaker>=1.6.4
    [SUCC] - >> run command : pip install Beaker>=1.6.4 success!
    [INFO] - >> run command : pip install MarkupSafe>=0.18
    [SUCC] - >> run command : pip install MarkupSafe>=0.18 success!
    [INFO] - >> run command : pip install PyYAML>=3.10
    [SUCC] - >> run command : pip install PyYAML>=3.10 success!
    [INFO] - >> run command : pip install bottle>=0.12.7
    [SUCC] - >> run command : pip install bottle>=0.12.7 success!
    [INFO] - >> run command : pip install tablib>=0.10.0
    [SUCC] - >> run command : pip install tablib>=0.10.0 success!
    [INFO] - >> run command : pip install nose
    [SUCC] - >> run command : pip install nose success!
    [INFO] - >> run command : pip install sh>=1.11
    [SUCC] - >> run command : pip install sh>=1.11 success!
    
选择是否安装mysql，如果你的系统已经安装mysql，或者使用外部mysql数据库，请选择不安装::

    [INFO] - start install mysql database server
    [INPUT] - install mysql, continue [y/n][n]y
    [INFO] - install mysql
    [INFO] - init mysql config
    [INFO] - write /var/toughradius/mysql/my.cnf
    [INFO] - >> run command : yum install -y mariadb mariadb-server mariadb-devel
    [SUCC] - >> run command : yum install -y mariadb mariadb-server mariadb-devel success!
    [INFO] - starting init mysql database
    [INFO] - >> run command : chown -R mysql:mysql /var/toughradius/mysql
    [SUCC] - >> run command : chown -R mysql:mysql /var/toughradius/mysql success!
    [INFO] - >> run command : mysql_install_db --defaults-file=/var/toughradius/mysql/my.cnf --user=mysql --datadir=/var/toughradius/mysql
    [SUCC] - >> run command : mysql_install_db --defaults-file=/var/toughradius/mysql/my.cnf --user=mysql --datadir=/var/toughradius/mysql  success!
    [INFO] - >> run command : mysqld_safe --defaults-file=/var/toughradius/mysql/my.cnf --user=mysql &
    [DEBUG] - 5
    [DEBUG] - 4
    [DEBUG] - 3
    [DEBUG] - 2
    [DEBUG] - 1
    150220 05:33:21 mysqld_safe Logging to '/var/toughradius/log/mysqld.log'.
    150220 05:33:21 mysqld_safe Starting mysqld daemon with databases from /var/toughradius/mysql
    [INFO] - >> run command : echo '30 1 * * * $(which toughctl) -backupdb -c /var/toughradius/radiusd.conf > /dev/null' > /tmp/backup.cron
    [SUCC] - >> run command : echo '30 1 * * * $(which toughctl) -backupdb -c /var/toughradius/radiusd.conf > /dev/null' > /tmp/backup.cron success!
    [INFO] - >> run command : crontab /tmp/backup.cron
    [SUCC] - >> run command : crontab /tmp/backup.cron success!
    
选择是否创建mysql管理用户，如果不需要，直接跳过::

    [INFO] - set mysql manage user
    [INPUT] - create a mysql admin user? y/n [n]y
    [INPUT] - set mysql manage username, not root [admin]:
    [INFO] - >> run command : set mysql manage passwd, [radius]:
    [SUCC] - >> run command : set mysql manage passwd, [radius]: success!
    [INFO] - >> run command : echo "GRANT ALL ON *.* TO admin@'%' IDENTIFIED BY 'radius' WITH GRANT OPTION;FLUSH PRIVILEGES" | mysql --defaults-file=/var/toughradius/mysql/my.cnf
    [SUCC] - >> run command : echo "GRANT ALL ON *.* TO admin@'%' IDENTIFIED BY 'radius' WITH GRANT OPTION;FLUSH PRIVILEGES" | mysql --defaults-file=/var/toughradius/mysql/my.cnf success!
    [INFO] - show database
    [INFO] - >> run command : echo "show databases;" | mysql --defaults-file=/var/toughradius/mysql/my.cnf
    [DEBUG] - 1
    Database
    information_schema
    mysql
    performance_schema
    test
    [INFO] - >> install centos depend done
    
安装ToughRADIUS包，根据你的网络情况，选择软件源镜像::
    
    [INFO] - start fetch ToughRADIUS from git repository
    [INPUT] - select ToughRADIUS mirror [ 1:github 2:oschina 3:coding 4:csdn ][1]:
    [INFO] - >> run command : git clone https://github.com/talkincode/ToughRADIUS.git /usr/local/toughradius
    [SUCC] - >> run command : git clone https://github.com/talkincode/ToughRADIUS.git /usr/local/toughradius success!
    [INFO] - >> run command : pip install -e /usr/local/toughradius
    [SUCC] - >> run command : pip install -e /usr/local/toughradius success!
    [INFO] - >> run command : ln -s $(which toughrad) /etc/init.d/toughrad
    [SUCC] - >> run command : ln -s $(which toughrad) /etc/init.d/toughrad success!
    [INFO] - >> run command : chmod +x /etc/init.d/toughrad
    [SUCC] - >> run command : chmod +x /etc/init.d/toughrad success!
    [INFO] - >> run command : chkconfig --add toughrad
    [SUCC] - >> run command : chkconfig --add toughrad success!
    [INFO] - >> run command : chkconfig toughrad on
    [SUCC] - >> run command : chkconfig toughrad on success!
    [INFO] - >> run command : chmod 754 /usr/lib/systemd/system/toughrad.service
    [SUCC] - >> run command : chmod 754 /usr/lib/systemd/system/toughrad.service success!
    
配置文件生成，根据你的实际环境进行配置::

    [INFO] - set config...
    [INFO] - set default option
    [INPUT] - set debug [0/1] [0]:
    [INPUT] - time zone [ CST-8 ]:
    [INFO] - set database option
    [INPUT] - database type [mysql]:
    [INPUT] - database host [127.0.0.1]:
    [INPUT] - database port [3306]:
    [INPUT] - database dbname [toughradius]:
    [INPUT] - database user [root]:
    [INPUT] - database passwd []:
    [INPUT] - db pool maxusage [30]:
    [INFO] - set mysql backup ftpserver option
    [INPUT] - backup ftphost [127.0.0.1]:
    [INPUT] - backup ftpport [21]:
    [INPUT] - backup ftpuser [ftpuser]:
    [INPUT] - backup ftppwd [ftppwd]:
    [INFO] - set radiusd option
    [INPUT] - radiusd authport [1812]:
    [INPUT] - radiusd acctport [1813]:
    [INPUT] - radiusd adminport [1815]:
    [INPUT] - radiusd cache_timeout (second) [600]:
    [INFO] - set admin option
    [INPUT] - admin http port [1816]:
    [INFO] - set customer option
    [INPUT] - customer http port [1817]:
    [SUCC] - config done
    
初始化数据库并启动服务::

    starting create and init database...
    drop database toughradius
    create database toughradius DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci
    commit
    [SUCC] - init db success
    [INFO] - start server...
    [INFO] - >> run command : toughrad start
    [SUCC] - >> run command : toughrad start success!
    [DEBUG] - 3
    [DEBUG] - 2
    [DEBUG] - 1
    [DEBUG] - 1
    # RUNNING 表示服务已经成功启动
    [INFO] - >> run command : toughrad status
    rad_console                      RUNNING   pid 2148, uptime 0:00:06
    rad_customer                     RUNNING   pid 2147, uptime 0:00:06
    radiusd                          RUNNING   pid 2153, uptime 0:00:05
    [INFO] - done


### 进程管理

通过以上步骤安装完成后，会提供一个进程管理工具 toughrad

启动ToughRADIUS进程::

    $ toughrad start

停止ToughRADIUS进程::

    $ toughrad stop

重启ToughRADIUS进程::

    $ toughrad restart
    
升级ToughRADIUS到最新版本::

    $ toughrad upgrade    

启动mysql数据库进程::

    $ toughrad startdb

停止mysql数据库进程::

    $ toughrad stopdb
    
备份ToughRADIUS主数据库,备份路径在/var/toughradius/databak,若要上传至ftp，请配置/var/toughradius/radiusd.json文件中的备份选项::

    $ toughrad backupdb

跟踪数据库日志::

    $ toughrad tracedb
    
跟踪radius日志::

    $ toughrad tracerad
    
跟踪管理控制台日志::

    $ toughrad traceadmin
    
跟踪自助服务控制台日志::

    $ toughrad tracecustomer    

## 使用Docker镜像 

在centos7下部署::

    $ yum install docker

    $ service docker start

    $ mkdir /var/toughradius

    $ docker run -d -v /var/toughradius:/var/toughradius \
      -p 3306:3306 -p 1812:1812/udp -p 1813:1813/udp \
      -p 1815:1815 -p 1816:1816 -p 1817:1817\
      --name toughradius talkincode/centos7-toughradius 

以上指令会在centos7中安装docker工具，并自动下载toughradius镜像以守护进程模式运行。

运行 docker logs toughradius 即可看到运行日志输出。


## web管理控制台的使用

当安装部署完成后可使用浏览器进入管理控制台进行操作。

默认地址与端口：http://serverip:1816
    
默认管理员与密码：admin/root

## 自助服务系统的使用

自助服务系统运行于一个独立的进程。

默认地址与端口:http://serverip:1817
