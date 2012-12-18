---
layout: pages
title: Install Rails Vim on Linux Ubuntu
description: Install Rails Vim on Linux Ubuntu
keywords: rails,vim,linux,ubuntu
---
___
###安装vim完全版。
    sudo apt-get install vim

___
###安装vim插件。
>参见：http://www.vim.org/scripts/script.php?script_id=1567

    NERD_tree.vim
    rails.vim
    lookupfile.vim
    genutils.vim
    snipMate.vim
    vcscommand.vim
___
###修改~/.vimrc，添加以下内容：
    "set guifont=Monaco\ 11
    set bsdir=buffer
    set enc=utf-8
    set fenc=utf-8
    set fencs=utf-8,ucs-bom,gb18030,gbk,gb2312,cp936
    syntax on
    set number
    set hlsearch
    set tabstop=4
    set cindent shiftwidth=4
    set autoindent shiftwidth=4
    filetype plugin indent on
    map &lt;F8&gt; :NERDTree&lt;CR&gt;
    "map &lt;C-S&gt; &lt;C-C&gt;:w&lt;CR&gt;

