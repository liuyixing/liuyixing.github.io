---
layout: post
title:  '怎么安装Jekyll'
date:   2016-04-27 16:30:00 +0800
categories: jekyll
---
### 怎么安装Jekyll？

其实[Jekyll官网][Jekyll官网]首页中间部分就给出了这个问题的答案。

![Jekyll快速入门指南][Jekyll快速入门指南]

依次执行上述4行命令，然后用浏览器访问http://localhost:4000。这样就行了？安装就是这么简单？

其实并不是，安装过程并不顺利，遇到了一些问题。

### 遇到了什么问题？

1、Unable to download data from https://rubygems.org/ - Errno::ECONNRESET: Connection reset by peer - SSL_connect (https://rubygems.org/latest_specs.4.8.gz)

> 原因：由于国内网络原因（你懂的），导致rubygems.org存放在Amazon S3上面的资源文件间歇性连接失败

> 解决：使用[淘宝RubyGems镜像][淘宝RubyGems镜像]，怎么使用？执行gem sources --add https://ruby.taobao.org/ --remove https://rubygems.org/  

2、ERROR:  While executing gem ... (Gem::FilePermissionError)
    You don't have write permissions for the /usr/bin directory.

> 原因：权限不足

> 解决：sudo gem install jekyll

3、ERROR:  Error installing jekyll:
        listen requires Ruby version >= 1.9.3.
        
> 原因：我使用的系统是Ubuntu 12.04，默认安装的Ruby版本过低，是1.8.7版本，可以执行ruby -v查看

> 解决：在[淘宝Ruby镜像库][淘宝Ruby镜像库]下载2.1稳定版，使用源码编译安装的方式，安装高版本的Ruby 

    curl https://ruby.taobao.org/mirrors/ruby/ruby-2.1-stable.tar.gz | tar xz
    cd ruby-2.1.10/
    ./configure
    make && sudo make install

4、Jekyll运行在172.19.104.157服务器上，我本地浏览器打开http://172.19.104.157:4000/无法访问

> 原因：Jekyll只监听了localhost，也就是127.0.0.1这个环回地址，而172.19.104.157地址没有被监听

> 解决：通过jekyll serve -h查看帮助文档，发现可以配置--host参数，所以通过jekyll serve --host=0.0.0.0方式重新启动Jekyll, 让Jekyll监听本机所有ip地址。另外，还可以在配置文件_config.yml中设置host: 0.0.0.0

Done!
Congratulations!
Enjoy it!

[Jekyll官网]: https://jekyllrb.com/
[淘宝RubyGems镜像]: https://ruby.taobao.org/
[淘宝Ruby镜像库]: https://ruby.taobao.org/mirrors/ruby/

[Jekyll快速入门指南]: http://7xtisb.com2.z0.glb.clouddn.com/images/howtoinstalljekyll/quickstart.jpg