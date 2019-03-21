# Notificatcher
Record some notifications into syslog for debugging
#### 捕获iOS里传递的各种notifications，根据它们的names和objects为线索来分析系统，是iOS逆向工程中常用手段之一。


* 为了达到这个目的，许多iOS逆向工程师的直观想法，是hook掉诸如postNotificationName:object:userInfo:、postNotification:、postNotificationName:object:userInfo:deliverImmediately:等函数，然后记录它们的参数。

* 但其实如果我们再深入一步，逆向看看上面3个函数的实现，就会发现它们底层调用的都是_CFXNotificationPost。这样的话，其实我们只用hook一个_CFXNotificationPost就可以达到目的了，代码更少了，实现更优雅，何乐而不为呢？
