---
layout: post
title:  "一体化教程: 如何在github pages上建博客"
date:   2019-11-04 11:01:36 +0530
---
本文教你如何使用Github pages + jekyll + VScode + Git建站。  

Github pages是github平台上的托管服务, 用户可以在github上托管博客/个人主页等静态网站。
按理来说一个Github账号只可以建立一个对应的Github pages网站, 但其实经过实验, <font color="#dd0000"><b>一个github账号是可以搭建多个github pages的</b></font>，详情请看文章末尾附录。  
关于github和git的基础知识不包含在本教程中, 所以文章默认读者拥有基本的git版本管理和github平台知识。关于构建过程中容易出错踩坑的地方我会着重给出。

## 1. 开启github pages
github pages的官方简单英文教程在官网 https://pages.github.com/ 可以查看。
  
先登陆自己的github账号, 建立一个新的public repository (注意，必须是public)。  
创建的repository的名字要求是username.github.io, 其中username是你github的账户名,

![github_account-w60](/pictures/blog1/pic1.jpg)

比如我本人的github地址为 https://github.com/Perryxubit , 则我需要建立名为
perryxubit.github.io的repository。  

注意1: 此处的username必须匹配你的账户名, 否则后续github pages不会识别  
注意2: 账户名是大小写不敏感的 (这个repository的名字就是日后访问的域名, 所以大小写不敏感)

## 2. 用git管理主页到本地
创建repository完成后使用git clone到本地。下面我们假设你的github账户名是perryxu:
```git
git clone https://github.com/perryxu/perryxu.github.io
cd perryxu.github.io
```
之后在文件夹内创建index.html, 为了测试, 我们在index.html填写简单显示内容, 提交到github上。
```git
git add .
git commit -m "initial check in"
git push -u origin master
```
在初次push到github上后， 需要等待一段时间 (几分钟到半小时不等), 然后在浏览器打开你的主页  
https://perryxu.github.io/  

此时你应该可以看到你提交的index.html里的内容了。
一个简单的github page搭建完毕。

## 3. 安装ruby/jekyll并搭建网站
虽然我们的网站搭建好了, 但是一个index.html实在简陋。如果你是优秀的前段开发工程师, 那你完全可以自己从0做一个想要的主页。如果你没有前段经验, 或者像我一样很懒, 那就和我一起用jekyll工具快速建个站吧。  

Jekyll是github pages官方推荐的工具, 可以用来快速搭建一个静态网站。 <b>简单来说jekyll就是基于Ruby的静态站点生成器。</b>
官方英文文档：https://help.github.com/en/github/working-with-github-pages/setting-up-a-github-pages-site-with-jekyll

既然基于Ruby, 那我们就要先安装ruby环境。
注意: 最新jekyll貌似需要Ruby 2.4.0以上的支持。
因为笔者用Mac自带Ruby, 本以为不用安装， 结果发现版本太久导致jekyll安装失败。 

重新安装ruby:
```bash
brew install ruby
export PATH=/usr/local/opt/ruby/bin:$PATH
ruby -v
```
确认版本正确后，安装jekyll和bundler. (bundler是Ruby中管理gem的工具, 而gem是Ruby中封装的代码包/库)
```bash
sudo gem install jekyll bundler
```
安装完成之后就可以在perryxu.github.io目录下运行jekyll建新的网站了：
```bash
jekyll new blog
```
等待片刻，我们的一个空的博客网站就在blog目录下生成了, 我们可以使用bundle来启动服务:
```bash
cd blog
bundle exec jekyll serve
```
注意: 服务启动默认端口为4000, 如果被占用请杀掉占用端口的程序或者修改端口
确保程序启动后，访问 http://localhost:4000 查看你的第一个博客吧!  

## 4. 下载使用更优秀的jekyll模板
使用jekyll new生成的博客不够炫酷，我们可以下载更多其他人写好的jekyll超炫酷模板。  
Jekyll模板下载地址：http://jekyllthemes.org/


下载完成后, 直接解压缩到git的perryxu.github.io目录下。  
注意: 直接解压所有文件到perryxu.github.io下, 不要再有子目录。

![directory](/pictures/blog1/pic3.jpg)


之后按照每个模板的要求进行更改：例如：
https://github.com/thelehhman/texture#Installation

注意: 主要修改的是_config.yml文件, 因为我们文件都放在根目录下, 所以_config.yml文件里baseurl要改成“”， 不然会出现ERROR: \\`not found的情况

修改完成后我们就可以build网站了，在根目录直接跑
```bash
bundle
```
然后等待构建即可。
<b>后续所有建立的新的markdown博客要建在_posts下。</b>

等博客修改完毕后, 再次启动本地server：
```bash
bundle exec jekyll serve
```
查看 http://localhost:4000 的效果满意后用git 提交, push到github中即可生效。

关于jekyll build出的静态站点结构会后续更新。

## 5. 使用VSCode编辑Markdown博客
编辑markdown工具很多，笔者最喜欢的就是轻量级的全栈编辑器-VS code.
使用VSCode的时候需要装一个Markdown All in One的插件, 就可以实时编辑/预览markdown文件了.
![vscode](/pictures/blog1/pic2.jpg)

md编辑效果：
![vscode_demo](/pictures/blog1/pic4.jpg)

## 6. 附录
### 同一个github创建多个github pages