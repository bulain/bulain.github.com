---
title: Linux下Subversion的搭建
layout: default
---

<div>Linux下Subversion的搭建</div>
<ol>
<li>安装Subversion。</li>
<ul>
<li>从安装源安装</li>
<pre>
sudo apt-get install subversion
</pre>

<li>测试Subversion的安装</li>
<pre>
sudo svnadmin create /home/svn
sudo groupadd subversion
sudo chown -R root:subversion /home/svn
sudo chmod -R g+rws /home/svn

mkdir svntest
echo "This is a test subversion" >> svntest/test.txt
svn import -m "new import" svntest file:///home/svn/svntest
</pre>
</ul>

<li>安装apache2服务器</li>
<ul>
<li>从安装源进行安装</li>
<pre>
sudo apt-get install apache2 
</pre>

<li>测试apache的安装</li>
<pre>
启动apache服务器：sudo /etc/init.d/apache2 start
打开浏览器，确认连接
http://localhost
确认是否正确显示信息。
</pre>
</ul>

<li>安装libapache2-svn</li>
sudo apt-get install libapache2-svn 

<li>配置Apache</li>
4.1 编辑/etc/apache2/httpd.conf
<pre>
<Location /svn>
  DAV svn
  SVNPath /home/svn
  AuthType Basic
  AuthName "subversion repository"
  AuthUserFile /etc/subversion/passwd
  AuthzSVNAccessFile /etc/subversion/authz
#  Satisfy Any 
  Require valid-user
</Location>
</pre>

4.2 添加用户
<pre>
sudo htpasswd -c /etc/subversion/passwd user1
</pre>

4.3 添加用户组
<pre>
编辑/etc/subversion/authz
[groups]
g_svn = user1, user2

[/]
@g_svn = r
svnroot = wr

[/svntest]
@g_svn = rw
</pre>

4.4 测试
<pre>
sudo /etc/init.d/apache2 restart
svn co http://localhost/svn/svntest svntest
浏览器访问：http://localhost/svn/svntest
</pre>

<li>配置https</li>
5.1 配置https
<pre>
a2enmod ssl
sudo mkdir /etc/apache2/ssl
cd /etc/apache2/ssl
sudo openssl req -x509 -newkey rsa:1024 -keyout apache.pem -out apache.pem -nodes -days 999 
编辑/etc/apache2/httpd.conf
<VirtualHost *:443>
  SSLEngine on
  SSLCertificateFile /etc/apache2/ssl/apache.pem
  SSLProtocol all
  SSLCipherSuite HIGH:MEDIUM
</VirtualHost>
</pre>

5.2 重启服务器，测试https
sudo /etc/init.d/apache2 restart
svn co https://localhost/svn/svntest svntest
浏览器访问：https://localhost/svn/svntest

</ol>
