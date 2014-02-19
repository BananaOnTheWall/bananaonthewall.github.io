---
layout: post
title:  Mac OSX Mavericks volume bitmap needs minor repair for orphaned blocks 问题解决方法
date:   2014-2-19 12:46:20
tags: mac
---
今天在检查硬盘的时候，意外收到了下面这样的提示：

{% highlight bash %}
Checking volume bitmap.
Volume bitmap needs minor repair for orphaned blocks
{% endhighlight %}

虽然不清楚这个问题背后的具体原因，但是也能知道，这是硬盘有了小问题。

一般来说，硬盘有了问题直接使用 Disk Utility 进行修复就好了。但是这次的问题在于，Repair Disk 那里灰掉了，也就是没法点击进行修复。

硬盘问题可大可小，不能存在侥幸心理。经过一系列折腾，终于找到了解决办法：

1. 进入系统设置下的 “Security and Privacy”，暂时关闭 “FileVault”。解密过程可能要花费一段时间。
2. 重启 Mac，再开机过程中按住 Cmd + R，进入安全模式。
3. 使用 Disk Utility 检查硬盘，这时候我们就能发现，在检查硬盘结束后，可以点击 “Repair Disk” 了。
4. 毫不犹豫的戳下去，进行修复。
5. 修复结束后，重启 Mac。
6. 已经搞定，没有第六步了。

至此，问题完美解决 :)