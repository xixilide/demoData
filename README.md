# 数据
###
```js
import axios from 'axios';
//用于请求数据，get 方法 post request response

function getJson(){
  let address=`https://raw.githubusercontent.com/xixilide/demoData/master/demo.json
  ?${Math.random()}`;
  //?${Math.random()用于查询
  return axios.get(address)
    .then((res) => ({

      getJson:res.data
    }))
    .catch(function (error) {
      alert(error);
    })
}
export { getJson };

```
### json 文件存储数据
```js
[
 {"title":"第一天","desc":"第一天描述","img":"http://obmf232cc.bkt.clouddn.com/home1.jpg","url":"a"},
 {"title":"第二天","desc":"第二天描述","img":"http://obmf232cc.bkt.clouddn.com/home2.jpg","url":"b"},
 {"title":"第三天","desc":"第三天描述","img":"http://obmf232cc.bkt.clouddn.com/home3.jpg","url":"c"},
 {"title":"第四天","desc":"第四天描述","img":"http://obmf232cc.bkt.clouddn.com/home4.jpg","url":"d"},
 {"title":"第五天","desc":"第五天描述","img":"http://obmf232cc.bkt.clouddn.com/home5.jpg","url":"e"}
]

```
### blog 用于存储分页面,每个页面不同跳转的内容
