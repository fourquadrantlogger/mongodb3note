```
命令行
--help	显示命令行参数
--nodb	不连接数据库方式启动，稍后可以使用 new Mongo() 或 connect() 来建立连接
--shell	从命令行运行完一个 .js 文件后，停留在shell中，而不是结束
特殊命令
非JavaScript的辅助指令：

help	显示帮助
db.help()	显示 db 方法帮助
db.myColl .help()	显示聚集的方法帮助
show dbs	打印服务器上所有数据库的列表
use dbname	设置db变量来指明使用服务器上的 dbname 数据库
show collections	打印当前数据库的所有聚集
show users	打印当前数据库的用户
show profile	打印最近耗时大于1ms的profiling操作
基本的Shell Javascript操作
db	指向当前数据库对象和连接的变量，已经在你的实例里定义好。
db.auth(user,pass)	数据库认证（如果运行安全模式的话）
coll = db.collection	访问数据库里特定的 collection
cursor = coll.find()	查找聚集里所有的对象。参考 [查询] 。
coll.remove(objpattern )	从聚集里删除匹配的对象。 
objpattern 是一个指定匹配的域的对象，例如：coll.remove( { name: "Joe" } );
coll.save(object )	在聚集中保存对象，如果已经存在的话则更新它。 
如果对象有 presave 方法，则会在保存到数据库之前（插入和更新之前）调用该方法。
coll.insert(object)	向聚集中插入对象。不会检查该对象是否已经存在聚集中（即，不是 upsert）
coll.update(...)	在聚集中更新对象。update() 有许多参数，请查看 更新 文档。
coll.ensureIndex( { name : 1 } )	对 name 建索引。如果索引存在则不做任何事。
coll.drop()	删除 coll 聚集
db.getSisterDB(name)	返回当前连接的另一个数据库。它允许跨数据库查询，例如：db.getSisterDB('production').getCollectionNames()
查询
coll.find()	查询所有文档
it	循环上次 find() 调用返回的游标
coll.find( criteria );	查询聚集中匹配 criteria 的对象。例如：coll.find( { name: "Joe" } );
coll.findOne( criteria);	查询并返回一个对象。如果没有找到则返回 null。如果你只需要返回一个对象，这个方法比 find() as limit(1) 效率更高。如果元素类型是字符串，数字或时间，你还可以使用正则表达式：coll.find( { name: /joe/i } );
coll.find( criteria, fields );	查询对象里特定的域。例如：coll.find( {}, {name:true} );
coll.find().sort( {field :1[, field :1] });	对返回结果进行排序（field ASC）。使用 -1 表示 DESC。
coll.find( criteria ).sort( { field : 1 } )	查找匹配 criteria 的对象，并对 field 进行排序。
coll.find( ... ).limit(n )	限制结果返回 n 行。如果你只需要某几行数据，推荐这样做来获得最优性能。
coll.find( ... ).skip(n)	跳过 n 行结果。
coll.count()	返回聚集里对象的总数。
coll.find( ... ).count()	返回匹配该查询的对象总数。注意，该返回会忽略 limit 和 skip。比如有100行记录匹配该查询，但是limit为10，count() 仍会返回100。这比你自己循环更快，但仍然需要消耗些时间。
更多信息请参考 [查询] 。

错误检查
[{{db.getLastError()}}]	返回上次操作的错误
db.getPrevError()	返回之前操作的错误
db.resetError()	清除错误记录
管理命令
db.cloneDatabase(fromhost)	从另外指定的主机拷贝当前数据数据库。fromhost必须为noauth模式。
db.copyDatabase(fromdb, todb, fromhost)	拷贝fromhost的fromdb数据库到当前服务器的todb数据库。fromhost必须为noauth模式。
db.repairDatabase()	修复当前数据库。如果数据库很大则该操作会非常慢。
db.addUser(user,pwd)	给当前数据库添加用户。
db.getCollectionNames()	获得所有聚集的列表。
db.dropDatabase()	删除当前数据库。
打开额外连接
db = connect("<host>:<port>/<dbname>")	打开一个新的数据库连接。一个shell可能有多个连接，但是shell自动的getLastError只用于 'db' 变量。
conn = new Mongo("hostname")	打开一个新的服务器连接。然后可以使用 getDB() 来选择一个数据库。
db = conn.getDB("dbname")	对一个连接选择一个特定的数据库。
```
