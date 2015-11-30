# go mongodb驱动

在golang官网（需要翻墙）
http://golang.org/ 找到了http://labix.org/mgo
还有其驱动源码地址：https://github.com/go-mgo/mgo

下载方法：

cd进入系统gopath

```
E:\golang.org\SYSGOPATH\src>go get gopkg.in/mgo.v2
```

接着在你的代码中
```
import “gopkg.in/mgo.v2”
```
查看代码文档

https://godoc.org/gopkg.in/mgo.v2

这篇文档太复杂，留着慢慢用：

1.回到http://labix.org/mgo

把这段代码copy并允许学习一下

注意把数据库地址改成本地：
```go
package main

import (
    "fmt"
    "log"
    "gopkg.in/mgo.v2"
    "gopkg.in/mgo.v2/bson"
)

type Person struct {
    Name string
    Phone string
}

func main() {
        session, err := mgo.Dial("127.0.0.1：")
        if err != nil {
                panic(err)
        }
        defer session.Close()

        // Optional. Switch the session to a monotonic behavior.
        session.SetMode(mgo.Monotonic, true)

        c := session.DB("test").C("people")
        err = c.Insert(&Person{"Ale", "+55 53 8116 9639"},
	               &Person{"Cla", "+55 53 8402 8510"})
        if err != nil {
                log.Fatal(err)
        }

        result := Person{}
        err = c.Find(bson.M{"name": "Ale"}).One(&result)
        if err != nil {
                log.Fatal(err)
        }

        fmt.Println("Phone:", result.Phone)
}
```

