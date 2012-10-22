---
title: Subversion Install On Ubuntu From Source
layout: default
---

<pre>
1，从源程序安装Apache
1.1 从源程序进行安装
sudo apt-get install openssl libssl-dev
下载Apache源程序，http://www.eng.lsu.edu/mirrors/apache/httpd/httpd-x.x.x.tar.gz
tar zxvf httpd-x.x.x.tar.gz
cd httpd-x.x.x
./configure --prefix=/usr/local/apache-x.x.x \
--enable-so \
--enable-auth-digest \
--enable-rewrite \
--enable-setenvif \
--enable-mime \
--enable-ssl \
--with-ssl=/usr/local \
--enable-dav \
--enable-headers
make
sudo make install

1.2 测试安装
export APACHE_HOME=/usr/local/apache-x.x.x
export PATH=$PATH:$APACHE_HOME/bin

启动apache服务器：apachectl -k start
打开浏览器，确认连接
http://localhost
确认是否正确显示信息。

2 从源程序安装Subversion
2.1 从源程序安装
下载subversion-x.x.x.tar.gz, http://subversion.tigris.org/downloads/subversion-x.x.x.tar.gz
安装之前可能需要安装zlib1g zlib1g-dev libexpat1 libexpat1-dev
sudo apt-get install zlib1g zlib1g-dev libexpat1 libexpat1-dev
tar zxvf subversion-x.x.x.tar.gz
cd subversion-x.x.x
./configure --prefix=/usr/local/subversion-x.x.x \
--with-apr=/usr/local/apache-x.x.x \
--with-apr-util=/usr/local/apache-x.x.x \
--with-apxs
make
sudo make install

2.2 测试Subversion安装
export SVN_HOME=/usr/local/subversion-x.x.x
export PATH=$PATH:$SVN_HOME/bin

sudo svnadmin create /home/svn
sudo groupadd subversion
sudo chown -R root:subversion /home/svn
sudo chmod -R g+rws /home/svn

mkdir svntest
echo "This is a test subversion" >> svntest/test.txt
svn import -m "new import" svntest file:///home/svn/svntest

</pre>
