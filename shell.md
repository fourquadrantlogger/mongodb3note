#使用MongoDB命令连接远程服务器的MongoDB数据库

MongoDB连接远程服务器的命令格式如下:
mongo 远程主机ip或DNS:MongoDB端口号/数据库名 -u user -p password
MongoDB连接远程服务器的命令示例代码如下:
//使用默认端口连接MongoDB
mongo 192.168.1.100
