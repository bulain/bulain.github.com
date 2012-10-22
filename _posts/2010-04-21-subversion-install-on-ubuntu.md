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
</ol>
