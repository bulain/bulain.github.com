---
layout: default
title: Apache JK with https
description: How to configure https on Apache and Tomcate JK
keywords: apache,jk,tomcat,https
---

___
###configuration with https
edit <apache_home>/conf/httpd.conf

    LoadModule ssl_module modules/mod_ssl.so 
    Include conf/extra/httpd-ssl.conf 
    <IfModule ssl_module>
    SSLRandomSeed startup builtin
    SSLRandomSeed connect builtin
    </IfModule>

edit <apache_home>/conf/extra/httpd-ssl.conf

    SSLCertificateFile "<apache_home>/conf/server.crt"
    SSLCertificateKeyFile "<apache_home>/conf/server.key"

___
###generate key and certification
    > cd <apache_home>/bin
    > openssl genrsa -out server.key 1024
    > openssl req -new –out server.csr -key server.key -config ../conf/openssl.cnf
    
    > openssl genrsa -out ca.key 1024
    > openssl req -new -x509 -days 365 -key ca.key -out ca.crt -config ../conf/openssl.cnf
    > openssl ca -in server.csr -out server.crt -cert ca.crt -keyfile ca.key -config ../conf/openssl.cnf
    
    > mkdir demoCA
    > touch demoCA/index.txt
    > echo 01 > demoCA/serial
    > mkdir demoCA/newcert
    
    > cp server.crt <apache_home>/conf
    > cp server.key <apache_home>/conf

___
###configration jk with https
edit <apache_home>/conf/httpd.conf

    LoadModule jk_module modules/mod_jk.so
    
    <IfModule jk_module>
    JkWorkersFile conf/workers.properties
    JkMountFile conf/uriworkermap.properties
    JkLogFile     logs/mod_jk.log
    JkLogLevel    info
    JkLogStampFormat "[%a %b %d %H:%M:%S %Y] "
    </IfModule>

edit <apache_home>/conf/extra/httpd-ssl.conf

    JkMountFile conf/uriworkermap.properties

edit <apache_home>/conf/uriworkermap.properties

    /test/*=load_balancer
    /jkstatus=jkstatus

edit <apache_home>/conf/workers.properties

    worker.list=load_balancer,jkstatus
    
    worker.server1.host=localhost
    worker.server1.port=8010
    worker.server1.type=ajp13
    worker.server1.lbfactor=1
    
    worker.load_balancer.type=lb
    worker.load_balancer.balanced_workers=server1
    worker.jkstatus.type=status
    