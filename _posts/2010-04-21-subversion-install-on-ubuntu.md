---
title: Linux下Subversion的搭建
layout: default
---

<div>Linux下Subversion的搭建</div>
<ol>
<li>安装Subversion。</li>
<pre>
1.1 从安装源安装
sudo apt-get install subversion

1.2 测试Subversion的安装
sudo svnadmin create /home/svn
sudo groupadd subversion
sudo chown -R root:subversion /home/svn
sudo chmod -R g+rws /home/svn

mkdir svntest
echo "This is a test subversion" >> svntest/test.txt
svn import -m "new import" svntest file:///home/svn/svntest
</pre>

<li>安装apache2服务器</li>
<pre>
2.1 从安装源进行安装
sudo apt-get install apache2 

2.2 测试apache的安装
启动apache服务器：sudo /etc/init.d/apache2 start
打开浏览器，确认连接
http://localhost
确认是否正确显示信息。
</pre>

<li>安装libapache2-svn</li>
<pre>
sudo apt-get install libapache2-svn 
</pre>

</ol>
