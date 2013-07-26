---layout: posttitle: Mac 无法休眠？看看哪些程序在让你的 Mac 无法休眠date: 2013-07-26excerpt: Mac 具有很强大的休眠模式，合上屏幕就会自动进入休眠，所以很多 Mac 用户平时都是个把月才会关一次机。但是偶尔也会电脑无法休眠的情况发生。通常这种情况发生的原因是后台有程序在保持运行，阻止电脑进入休眠。那么找出并杀死这些程序就显得很重要。tags: apps---
Mac 具有很强大的休眠模式，合上屏幕就会自动进入休眠，所以很多 Mac 用户平时都是个把月才会关一次机。但是偶尔也会电脑无法休眠的情况发生。通常这种情况发生的原因是后台有程序在保持运行，阻止电脑进入休眠。那么找出并杀死这些程序就显得很重要。

其实在 Mac 下可以通过命令行快速的发现到底是哪些程序在阻止 Mac 休眠。打开终端，输入如下命令：

{% highlight bash%}
pmset -g assertions
{% endhighlight%}

返回的信息中，terminal 上方显示的是类似于下面这样的内核断言信息：

{% highlight bash%}
Assertion status system-wide:
   PreventUserIdleDisplaySleep    0
   PreventSystemSleep             0
   PreventUserIdleSystemSleep     1
   ExternalMedia                  0
   UserIsActive                   0
   ApplePushServiceTask           0
   BackgroundTask                 0
{% endhighlight%}

0 代表没有激发，1代表已经被激发。

在下方可能会有下面这样的信息：

{% highlight bash%}
Listed by owning process:
  pid 9022(iTunes): [0x0000000100001192] 00:18:23 PreventUserIdleSystemSleep named: "Nameless (via IOPMAssertionCreate)" 
  pid 198(coreaudiod): [0x0000000100001287] 00:12:39 NoIdleSleepAssertion named: "com.apple.audio.'AppleHDAEngineOutput:1B,0,1,2:0'.noidlesleep" 
{% endhighlight%}

让你的电脑无法休眠的罪魁祸首通常就隐藏在上面这段信息中。比如上面的信息就表示，是 pid 9022 和 pid 198 这两个进程让你的 Mac 不能休眠。其中第一个貌似和 iTunes 有关，可能是因为你正在听音乐，第二个是 coreoudiod，看名字也像是和音频播放有关系的进程。

如果通过进程的名称无法联想到是什么程序在作怪，你还可以通过 Activity Monitor 来查看这些 pid 到底和哪些 app 有关，然后就可以放心的干掉这些让你的 Mac 无法休眠的app了。

May your Mac sleep well...



