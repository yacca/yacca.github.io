---
layout: post
title: 用 Jekyll 在 Github 上搭建个人博客
---

### 在 Mac OS X 上安装 Ruby

利用 RVM 安装 Ruby
{% highlight bash %}
$ curl -L https://get.rvm.io | bash -s stable --ruby
{% endhighlight %}

在此过程中有些依赖的软件包无法自动安装，需要手动用 homebrew 来安装


### 安装 Jekyll
{% highlight bash %}
$ gem install jekyll
{% endhighlight %}


### 创建 Jekyll 站点
{% highlight bash %}
$ jekyll new myblog
{% endhighlight %}

