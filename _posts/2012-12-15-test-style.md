---
layout: default
title: Test Style
description: Test Style
keywords: css,github
---

#Markdown语法说明

___
###标题写法
#Title 1
##Title 2
###Title 3
####Title 4
#####Title 5
######Title 6

___
###列表写法
无序列表

* test 1
* test 2
* test 3

有序列表

0. test 1
0. test 2
0. test 3


___
###代码区块写法
    /*
     * 样式写法
     */
    .sl-rgba{
        background:rgba(0, 0, 0, 0.3);
    }

    #命令写法
    git add . 
    git commit -m 'comments'
    git push -u origin master

    //代码写法
    private static ExecutorService getExecutorService() {
        if (executorService != null) {
            return executorService;
        }

        return executorService;
    }


___
###引用写法
>mail test 1

>mail test 2

___
###链接写法
This is inline link 1. <http://www.google.com>

This is inline link 2. [Index](/index.html "Index")

This is inline link 3. [Google](http://www.google.com "Google")

This is referance link 1. [Google][1]

This is referance link 2. [Google][link1]

This is referance link 3. [Google][]

  [1]: http://www.google.com "Google"
  [link1]: http://www.google.com "Google"
  [Google]: http://www.google.com "Google"

___
###强调写法
*single asterisks*

**double asterisks**

___
###代码写法
Use the `printf()` function.


___
###图片写法
![inline picture](/shared/bootstrap/img/glyphicons-halflings.png)

![referance picture][pic1]

[pic1]: /shared/bootstrap/img/glyphicons-halflings.png  "referance picture"

