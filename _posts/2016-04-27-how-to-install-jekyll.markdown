---
layout: post
title:  '怎么安装Jekyll'
date:   2016-04-27 16:30:00 +0800
categories: jekyll
---
怎么安装Jekyll？其实[Jekyll官网][Jekyll官网]首页中间部分有给出了快速入门指南。
![Jekyll快速入门指南](https://raw.githubusercontent.com/liuyixing/liuyixing.github.io/master/images/howtoinstalljekyll/01.png)

依次执行上述4行命令，没错！安装就是这么简单。

咋看，貌似这篇文章需要讲的东西已经讲完了。非也，安装过程其实并不顺利，遇到了一些问题，所以写了这篇文章，记录下来。

遇到的问题
1. Unable to download data from https://rubygems.org/ - Errno::ECONNRESET: Connection reset by peer - SSL_connect (https://rubygems.org/latest_specs.4.8.gz)
原因：由于国内网络原因（你懂的），导致 rubygems.org 存放在 Amazon S3 上面的资源文件间歇性连接失败。
解决：使用淘宝 RubyGems 镜像 https://ruby.taobao.org/，怎么使用？执行gem sources --add https://ruby.taobao.org/ --remove https://rubygems.org/


[Jekyll官网]: https://jekyllrb.com/