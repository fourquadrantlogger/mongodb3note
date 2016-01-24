```  shell
默认的情况下，关闭shell，mongodb就停止运行了。

如果想在后台运行，启动时只需添加 --fork函数即可。

可以在日志路径后面添加--logappend，防止日志被删除。

bin/mongodb  --fork --dbpath=//  --logpath=//  --logappend

在后台运行，如果想要关闭它的话，需要给他发送shutdownServer()

1、普通命令：
$ ./mongod
> use admin
> db.shutdownServer()

```
