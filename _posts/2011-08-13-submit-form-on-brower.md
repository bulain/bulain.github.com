---
layout: pages
title: 浏览器默认回车键触发表单提交
description: 浏览器默认回车键触发表单提交
keywords: firefox,IE,chrome
---

___
###前提：
    submit写法：<intput type='submit'/>, <button type='submit'/>
    button写法：<intput type='button'/>, <button type='button'/>
    text写法：<intput type='text'/>

___
###结论:
    1. 当form中至少有一个submit时，回车键生效。
    2. 当form中只有一个text时，回车键生效。
    3. 当按钮使用<input>，而是用<button>，并且没有加type，IE下默认为type=button，Firefox默认为type=submit。
    4. 其他form元素如textarea、select不影响，radio checkbox不影响触发规则，但本身在Firefox下会响应回车键，在IE下不响应。
    5. type=”image”的input，效果等同于type=”submit”，但后面会跟一个X=&Y=的坐标。