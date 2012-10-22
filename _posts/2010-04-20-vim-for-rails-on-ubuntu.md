---
title: Linux Ubuntu下Rails Vim环境的搭建
layout: default
---

<div>Linux Ubuntu下Rails Vim环境的搭建</div>
<ol>
<li>安装vim完全版。</li>
<pre>
sudo apt-get install vim
</pre>

<li>安装vim插件。</li>
<pre>
参见：http://www.vim.org/scripts/script.php?script_id=1567
NERD_tree.vim
rails.vim
lookupfile.vim
genutils.vim
snipMate.vim  
vcscommand.vim  
</pre>

<li>修改~/.vimrc，添加以下内容：</li>
<pre>
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
map <F8> :NERDTree<CR>
"map <C-S> <C-C>:w<CR>
</pre>
</ol>