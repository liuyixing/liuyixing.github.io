---
layout: post
title:  '怎么安装Jekyll'
date:   2016-04-27 16:30:00 +0800
categories: jekyll
---
怎么安装Jekyll？其实[Jekyll官网][Jekyll官网]首页中间部分就给出了快速入门指南。
![Jekyll快速入门指南](https://raw.githubusercontent.com/liuyixing/liuyixing.github.io/master/images/howtoinstalljekyll/01.jpg)

依次执行上述4行命令，然后就行了？安装就是这么简单？貌似这篇文章需要讲的东西都已经讲完了。

其实并没有，安装过程并不顺利，遇到了一些问题，所以写下这篇文章，记录下来。

遇到的问题
1. Unable to download data from https://rubygems.org/ - Errno::ECONNRESET: Connection reset by peer - SSL_connect (https://rubygems.org/latest_specs.4.8.gz)
原因：由于国内网络原因（你懂的），导致 rubygems.org 存放在 Amazon S3 上面的资源文件间歇性连接失败。
解决：使用淘宝 RubyGems 镜像 https://ruby.taobao.org/，怎么使用？执行gem sources --add https://ruby.taobao.org/ --remove https://rubygems.org/

2. ERROR:  While executing gem ... (Gem::FilePermissionError)
    You don't have write permissions for the /usr/bin directory.
原因：权限不足
解决: sudo gem install jekyll

3.ERROR:  Error installing jekyll:
        listen requires Ruby version >= 1.9.3.
原因: 我使用的系统是Ubuntu 12.04，默认安装的ruby版本过低，可以执行ruby -v查看ruby版本
ruby 1.8.7 (2011-06-30 patchlevel 352) [x86_64-linux]
解决: 使用源码编译安装的方式，安装高版本的ruby
ruby官网下载地址 https://www.ruby-lang.org/en/downloads/mirrors/
ruby淘宝镜像库 https://ruby.taobao.org/mirrors/ruby/
选择2.1稳定版 https://ruby.taobao.org/mirrors/ruby/ruby-2.1-stable.tar.gz
{% highlight ruby %}
curl https://ruby.taobao.org/mirrors/ruby/ruby-2.1-stable.tar.gz | tar xz
cd ruby-2.1.10/
./configure
make && sudo make instal
{% endhighlight %}

4.Jekyll运行在172.19.104.157服务器上，我本地浏览器打开http://172.19.104.157:4000/无法访问
原因: Jekyll只listen在localhost
解决: Jekyll serve -h查看帮助文档，发现可以配置-h参数，重新运行jekyll serve --host=0.0.0.0
或者在配置文件_config.yml中设置host: 0.0.0.0

[Jekyll官网]: https://jekyllrb.com/