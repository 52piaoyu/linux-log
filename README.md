# linux-log

一、  当客户端系统为linux时。
在linux下面相对简单，可以采用以下命令登陆，不会在w、 last、 lastlog里面留下痕迹：

ssh -o UserKnownHostsFile=/dev/null -T user@host /bin/bash -i
或者：

ssh -o UserKnownHostsFile=/dev/null -luser host /bin/bash -i
如果目标更改了端口，在host后面加上 -p 端口就可以了。


登陆之后，记得先执行以下的命令，清除当前会话所有缓存：
 

unset HISTFILE;unset HISTSIZE;unset HISTORY;unset HISTSAVE;unset HISTFILESIZE

遇到需要交互的时候，可以用python模拟出一个pty：
 

python -c 'import pty;pty.spawn("/bin/sh")'

模拟pty之后再清除当前会话所有缓存：
 

unset HISTFILE;unset HISTSIZE;unset HISTORY;unset HISTSAVE;unset HISTFILESIZE

这样子，在w、 last、 lastlog命令里面都无法查看到我们登陆。
 
不过依然会在/var/log/目录下面的日志里留下登陆成功或者失败的记录。这个痕迹的删除我们先把 windows下面隐藏登陆痕迹讲完之后再详细列出。

 来源：https://weibo.com/ttarticle/p/show?id=2309404729848538202699
