---
layout: default
title: Installing ReviewBoard on Ubuntu
description: Installing ReviewBoard on Ubuntu
keywords: reviewboad,linux,ubuntu
---

###Installing Setuptools
    # apt-get install python-setuptools

###Installing Python Development Headers
    # apt-get install python-dev

###Installing Memcached
    # apt-get install memcached
    # apt-get install python-memcached

###Installing Patch
    # apt-get install patch

###Installing Python LDAP
    # apt-get install python-ldap

###Installing Mysql
    # apt-get install mysql-server
    # apt-get install mysql-client
    # apt-get install python-mysqldb
    # mysql -u root -p
    > create database reviewboard;
    > grant all on reviewboard.* to reviewboard@localhost identified by 'reviewboard';

###Installing Subversion
    # apt-get install subversion 
    # apt-get install python-svn

###Installing Git
    # apt-get install git-core

###Installing ReviewBoard
    # wget http://downloads.reviewboard.org/releases/ReviewBoard/1.6/ReviewBoard-1.6.1.tar.gz
    # tar zxvf ReviewBoard-1.6.1.tar.gz
    # cd ReviewBoard-1.6.1
    # python ./setup.py install

###Installing Site
    # rb-site install /usr/local/reviewboard
    # chown -R www-data /usr/local/reviewboard/htdocs/media/uploaded
    # chown -R www-data /usr/local/reviewboard/data
    // Config site with apache or lighttpd using reviewboard/conf/*.conf

###Installing post-review
    # wget http://downloads.reviewboard.org/releases/RBTools/0.3/RBTools-0.3.4.tar.gz
    # tar zxvf RBTools-0.3.4.tar.gz
    # cd RBTools-0.3.4
    # python ./setup.py install
    