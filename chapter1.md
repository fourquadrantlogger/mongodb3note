# windows安装

下载地址：
https://www.mongodb.org/downloads?_ga=1.4783411.1275976618.1448610369

安装位置：随意，我按照到了E://program files/Mongodb

随后打开mongodb文档
https://docs.mongodb.org/manual/tutorial/install-mongodb-on-windows/

设置一个数据库路径

你的安装文件夹...\mongod.exe --dbpath E:\mongodb.org\DB

我安装到了E:\mongodb.org\DB

```
E:\Program Files\MongoDB\Server\3.0\bin>mongod.exe --dbpath e:\mongodb.org\DB
2015-11-30T09:56:30.644+0800 I JOURNAL  [initandlisten] journal dir=e:\mongodb.org\DB\journal
2015-11-30T09:56:30.683+0800 I JOURNAL  [initandlisten] recover : no journal files present, no recovery needed
2015-11-30T09:56:30.950+0800 I JOURNAL  [durability] Durability thread started
2015-11-30T09:56:31.011+0800 I JOURNAL  [journal writer] Journal writer thread started
2015-11-30T09:56:31.056+0800 I CONTROL  [initandlisten] MongoDB starting : pid=5628 port=27017 dbpath=e:\mongodb.org\DB 64-bit host=lipeng-dell
2015-11-30T09:56:31.057+0800 I CONTROL  [initandlisten] targetMinOS: Windows 7/Windows Server 2008 R2
2015-11-30T09:56:31.058+0800 I CONTROL  [initandlisten] db version v3.0.7
2015-11-30T09:56:31.058+0800 I CONTROL  [initandlisten] git version: 6ce7cbe8c6b899552dadd907604559806aa2e9bd
2015-11-30T09:56:31.059+0800 I CONTROL  [initandlisten] build info: windows sys.getwindowsversion(major=6, minor=1, build=7601, platform=2, service_pack='Service Pack 1') BOOST_LIB_VERSION=1_49
2015-11-30T09:56:31.060+0800 I CONTROL  [initandlisten] allocator: tcmalloc
2015-11-30T09:56:31.061+0800 I CONTROL  [initandlisten] options: { storage: { dbPath: "e:\mongodb.org\DB" } }
2015-11-30T09:56:31.065+0800 I INDEX    [initandlisten] allocating new ns file e:\mongodb.org\DB\local.ns, filling with zeroes...
2015-11-30T09:56:31.468+0800 I STORAGE  [FileAllocator] allocating new datafile e:\mongodb.org\DB\local.0, filling with zeroes...
2015-11-30T09:56:31.468+0800 I STORAGE  [FileAllocator] creating directory e:\mongodb.org\DB\_tmp
2015-11-30T09:56:31.534+0800 I STORAGE  [FileAllocator] done allocating datafile e:\mongodb.org\DB\local.0, size: 64MB,  took 0.007 secs
2015-11-30T09:56:31.552+0800 I NETWORK  [initandlisten] waiting for connections on port 27017
2015-11-30T09:57:12.032+0800 I NETWORK  [initandlisten] connection accepted from 127.0.0.1:55725 #1 (1 connection now open)
```
启动客户端mongo.exe
```
E:\Program Files\MongoDB\Server\3.0\bin>mongo.exe
MongoDB shell version: 3.0.7
connecting to: test
Welcome to the MongoDB shell.
For interactive help, type "help".
For more comprehensive documentation, see
        http://docs.mongodb.org/
Questions? Try the support group
        http://groups.google.com/group/mongodb-user
```