---
layout: pages
title: rhel-6.2下ISO文件作为yum更新源
description: rhel-6.2下ISO文件作为yum更新源
keywords: redhat,yum,iso
---

###1. 挂载ISO文件。
    mount -t iso9660 -o loop /home/bulain/rhel/rhel-server-6.2-x86_64-dvd.iso /mnt/iso

###2. 将yum源指向挂载文件。
    mv /etc/yum.repos.d/rhel-source.repo /etc/yum.repos.d/rhel-source.repo.bak
    vim /etc/yum.repos.d/yum.repo
    [cd]
    name=cd
    baseurl=file:///mnt/iso
    enabled=1
    gpgcheck=0