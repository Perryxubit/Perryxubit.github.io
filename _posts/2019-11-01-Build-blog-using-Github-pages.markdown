---
layout: post
title:  "用github pages和jekyll建站"
date:   2019-11-04 11:01:36 +0530
---
使用Github pages + jekyll + VScode建站

github pages是github上的托管服务, 可以托管github上的博客/主页等静态网站。


jekyll模板下载地址：
http://jekyllthemes.org/


下载完成后, 直接解压缩到git的username.github.io目录下 (不要再有子目录)
![directory](/pictures/20191101/pic1.jpg)

然后按照模板要求进行更改：例如：
https://github.com/thelehhman/texture#Installation


baseurl要改成 “”的形式， 不然回出现ERROR: \\`not found的情况

启动本地server：
```bash
bundle exec jekyll serve
```



Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
