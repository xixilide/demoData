# 我是C页面--用于记录bootstrap的笔记

### 引入bootstrop

```js
import 'bootstrap/dist/css/bootstrap.min.css';
```
### content.js 将卡片组件化

```js
import React, { PropTypes } from 'react';
import { Link} from 'react-router';
import Card from './component/card';
import Img1 from './images/1.jpg';
import Img2 from './images/2.jpg';
import Img3 from './images/3.jpg';
let cardData=[
  {title:'第一天',desc:'第一天描述',img:Img1,url:'a'},
  {title:'第二天',desc:'第二天描述',img:Img2,url:'b'},
  {title:'第三天',desc:'第三天描述',img:Img3,url:'c'},
  {title:'第四天',desc:'第四天描述',img:Img3,url:'d'}
]

class Content extends React.Component {
  render () {
  return(

    <div className="container-fluid">
        <div className="row" style={{marginTop:'20px'}}>
            {cardData.map( (item,i) => <Card {...item} key={i} />)}
            //通过map箭头函数将数组全部传到卡片中
        </div>

</div>
  )
  }
}

export default Content;
```
### card.js

```js
import React, { PropTypes } from 'react';
import {  browserHistory} from 'react-router';
class Card extends React.Component {
  handleJump(){
    let address=this.props.url;
    browserHistory.push(`/blog/${address}`)
  }
  render () {
return(
  <div className="col-xs-6 col-md-4">
    <div className="thumbnail">
      <img src={this.props.img}  />
      <div className="caption">
        <h3>{this.props.title}</h3>
        <p>{this.props.desc}</p>
        <p><a className="btn btn-primary" role="button" onClick={this.handleJump.bind(this)}>Button</a></p>
      </div>
    </div>

  </div>
  )


  }
}
Card.defaultPraps={
  title:'我是标题',
  desc:'我是描述',
  url:'a'
}
export default Card;
```
