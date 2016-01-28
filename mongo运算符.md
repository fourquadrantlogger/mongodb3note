
## 删除字段
db.User.update({email:'admin@linkris.com'},{$unset:{'attributes.birthday':''}})
## 修改字段
db.test.update({}, {$rename : {"abc" : "def"}}, false, true)
