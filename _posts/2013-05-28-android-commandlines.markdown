---
layout: post
title: Android 命令行工具
---

### 清除某个应用（package）相关数据
{% highlight bash %}
$ adb shell pm clear package.name
{% endhighlight %}

### 通过 Action 来启动 Activity
{% highlight bash %}
$ adb shell am start -a "com.orange.messenger"
{% endhighlight %}

### 通过 Component 来启动 Activity
{% highlight bash %}
$ adb shell am start -n "com.orange.messenger/com.orange.messenger.SplashScreen"
{% endhighlight %}

### 通过进程 id 或者应用包名查看内存使用信息
{% highlight bash %}
$ adb shell dumpsys meminfo <package_name|pid>
{% endhighlight %}

### 查看 CPU 信息
{% highlight bash %}
$ adb shell dumpsys cpuinfo
{% endhighlight %}

### 查看 Activity 信息
{% highlight bash %}
$ adb shell dumpsys activity
{% endhighlight %}

### 查看 Activity 信息
{% highlight bash %}
$ # set operator, 20801 for OFR, 310260 for T-Mobile USA
$ adb shell setprop gsm.sim.operator.numeric 20801
$ adb shell setprop gsm.operator.numeric 20801
{% endhighlight %}
