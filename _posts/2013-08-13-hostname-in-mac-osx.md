---
layout: post
title: Mac OS X 中 hostname 的设置
---

## 查看系统 hostname 设置

使用命令行工具 hostname 可以查看系统 hostname 设置：
{% highlight bash %}
$ hostname
{% endhighlight %}

它的值会按优先级依次取决于下列值：
 * hostname 命令设置的值
 * HostName 属性值
 * LocalHostName 属性值（通常系统都会设置此属性）

关于 hostname 相关属性，scutil 命令手册（info scutil 或 man scutil）中有如下描述：
>               ComputerName   The user-friendly name for the system.
>
>               LocalHostName  The local (Bonjour) host name.
>
>               HostName       The name associated with hostname(1) and
>                              gethostname(3).

-----------------

## 设置 hostname
有三种方式设置 hostname：
 * System Preferences
 * 命令行工具 hostname
 * 命令行工具 scutil

### System Preferences
设置方法：
>  System Preferences -> Sharing
在这里可以查看和设置 *ComputerName* 和 *LocalHostName*，但不能设置 *HostName* 的值。

对于普通用户通常使用这种方式就可以了，因为通常情况下都没有用 hostname 和 scutil 来设置，所以就会取 *LocalHostName* 的值。

### 命令行工具 hostname
设置当前系统的 hostname 为 MyMac：
{% highlight bash %}
$ hostname MyMac
{% endhighlight %}
*注意：这种方式不能保持到重启后*

根据 hostname 命令的手册（info hostname 或 man hostname），可以使用 scutil 命令来持久修改 hostname

### 命令行工具 scutil
查看各属性值：
{% highlight bash %}
$ sudo scutil --get ComputerName
Yanke's MBP
$ sudo scutil --get LocalHostName
Yankes-MBP
$ sudo scutil --get HostName
HostName: not set
{% endhighlight %}

设置 HostName 属性值：
{% highlight bash %}
scutil --set HostName MyMac
{% endhighlight %}

scutil 可以修改 *ComputerName*，*LocalHostName* 和 *HostName* 任意一个值。

