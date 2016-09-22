# 我是A页面-记录marked的笔记

### 导入marked包，用于.md文件

```js
import marked from 'marked';
console.log(marked('I am using __markdown__.'));

```
****
<!-- 分割线 -->
### .md文件的用法

```js

import marked from 'marked';
console.log(marked('I am using __markdown__.'));

class Marked extends React.Component {
  render () {
    let content=marked('# abc')
  return(
    <div>
      <div dangerouslySetInnerHTML={{__html:content}} />
    </div>
  )

  }
}

export default Marked;
```

****
### 通过md文件的github地址来实现分页

```js
function getMd(add){
  // add为传的地址title参数
  let address=`https://raw.githubusercontent.com/xixilide/demoData/master/blog/${add}.md`;
  return axios.get(address)
    .then((res) => ({

      getMd:res.data
    }))
    .catch(function (error) {
      alert(error);
    })
}
```
