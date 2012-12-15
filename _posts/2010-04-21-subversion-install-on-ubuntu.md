---
layout: default
title: Install Subversion on Linux Ubuntu
description: Install Subversion on Linux Ubuntu
keywords: subversion,linux,ubuntu
---

###Install Subversion on Linux Ubuntu

___
###1 安装Subversion。
1-1 从安装源安装

    sudo apt-get install subversion

1-2 测试Subversion的安装

    sudo svnadmin create /home/svn
    sudo groupadd subversion
    sudo chown -R root:subversion /home/svn
    sudo chmod -R g+rws /home/svn

    mkdir svntest
    echo "This is a test subversion" &gt;&gt; svntest/test.txt
    svn import -m "new import" svntest file:///home/svn/svntest

___
###2 安装apache2服务器
2-1 从安装源进行安装

    sudo apt-get install apache2 

2-2 测试apache的安装

    启动apache服务器：
    sudo /etc/init.d/apache2 start
    打开浏览器，确认连接
    http://localhost
    确认是否正确显示信息。

___
###3 安装libapache2-svn
    sudo apt-get install libapache2-svn 

___
###4 配置Apache
4-1 编辑/etc/apache2/httpd.conf

    &lt;Location /svn&gt;
      DAV svn
      SVNPath /home/svn
      AuthType Basic
      AuthName "subversion repository"
      AuthUserFile /etc/subversion/passwd
      AuthzSVNAccessFile /etc/subversion/authz
      #Satisfy Any 
      Require valid-user
    &lt;/Location&gt;

4-2 添加用户

    sudo htpasswd -c /etc/subversion/passwd user1

4-3 添加用户组

    编辑/etc/subversion/authz
    [groups]
    g_svn = user1, user2    
    [/]
    @g_svn = r
    svnroot = wr    
    [/svntest]
    @g_svn = rw

4-4 测试

    sudo /etc/init.d/apache2 restart
    svn co http://localhost/svn/svntest svntest
    浏览器访问：
    http://localhost/svn/svntest

___
###5 配置https
5-1 配置https

    a2enmod ssl
    sudo mkdir /etc/apache2/ssl
    cd /etc/apache2/ssl
    sudo openssl req -x509 -newkey rsa:1024 -keyout apache.pem -out apache.pem -nodes -days 999 

5-2 编辑/etc/apache2/httpd.conf

    &lt;VirtualHost *:443&gt;
      SSLEngine on
      SSLCertificateFile /etc/apache2/ssl/apache.pem
      SSLProtocol all
      SSLCipherSuite HIGH:MEDIUM
    &lt;/VirtualHost&gt;

5-3 重启服务器，测试https

    sudo /etc/init.d/apache2 restart
    svn co https://localhost/svn/svntest svntest
    浏览器访问：
    https://localhost/svn/svntest


