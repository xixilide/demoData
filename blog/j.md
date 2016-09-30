# 关于mongoos的知识
[mongoose主页](http://mongoosejs.com/)
 mongoose 将数据记录封装成对象

#### first step install package mongoose
$ npm install mongoose --save

#### leading-in mongoose
- var mongoose = require('mongoose');

### mongodb 协议链接，connection SQL
- mongoose.connect('mongodb://localhost:27017/persons');
//SQL is persons
#### get this connection，save in db
```js
- var db = mongoose.connection;

- db.on('error', console.error.bind(console, 'connection error:'));
- db.once('open', function() {
-   console.log("seccuss");
});

  //connection success!
```
### defined Schema

- var kittySchema = mongoose.Schema({
    name: String

    //discribe data  type

  });

每个项目只需要一个schema
mongoose.Schema() //一条记录  With Mongoose, everything is derived from a Schema.

```
  - Schema 概要 描述数据结构  记录中有几个字段（field），每个字段的名字(name),
  - reference 指针/参考文献
  - property 属性
  - MVC 模型视图控制器 Model view Controlier 软件架构
    - model 中存放所有和数据直接相关的代码，通常会写成一个类
```
#### The next step is compiling our schema into a Model.

- var Person = mongoose.model('Persons', PersonSchema);
//定义一个model 实际一条记录的名字（'Persons'）为数据库
#### 写一条记录
var Me = new Person({ name: 'Yan' });

console.log(Me.name);
// 打印出记录名字 'Yan'

#### 保存数据库记录
   Me.save()

### 代码实例
```js
var mongoose = require('mongoose');

mongoose.connect('mongodb://localhost:27017/persons');

var db = mongoose.connection;

var PersonSchema = mongoose.Schema({
    name: String

});
db.once('open', function() {
  console.log("success");
});
var Persons = mongoose.model('Persons',PersonSchema);

var Yan = new Persons({name:"xixilide"})
Yan.save();

console.log(Yan.name);

persons.find().exec(function(err, persons) {
    // 异步执行
    console.log(persons);
  });
})

```
### 异步操作
```js
persons.find().exec(function(err, persons) {
    // 异步执行
    console.log(persons);
  });
```

### 第四步.用数据库的形式对数据进行增删改查
- 增：name.save();
- 删：name.remove();
- 查：persons.find();//必须在一个model上的user（代
     表一个集合）
    - find（）；展示所有
    - Persons.find({ name: /^fluff/ }, callback);查找符合条件的
- 改：update
      peter.name = 'peterpeter',
      peter.password = 'aaabbb',
      peter.save()
#### 增加操作
```js
var user = new Persons({
  name:"xixilide",
  password:123,
  age:20
});
user.save();

console.log(user);
```
#### 更新操作
```js
Persons.findById({_id: '57ec8894e195c50dadbb996a'}, function(err, user) {
  user.name = 'new'
  user.save(function(err){
    console.log('更新了！')
    Persons.find().exec(function(err, user) {
      // 异步执行
      console.log(Persons);
    });
  });

})
console.log("我先出来了")
```
//先输出 “我先出来了”，再打印出更新了
#### 删除操作
删除id号的一条记录
```js
Persons.findById({_id: '57ec8894e195c50dadbb996a'}, function(err, user) {
  user.name = 'new'
  user.remove(function(err){
    console.log('删除了')
    Persons.find().exec(function(err, users) {
      // 异步执行
      console.log(users);
    });
  });
})
```
