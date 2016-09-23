# 我是E页面--记录react生命周期

### racte生命周期

```js
class App extends React.Component {
  getDefaultProps(){
    // console.log("获取默认属性值");
  }
  getInitialState(){
    // console.log("获取实例初始状态");
  }
  componentWillMount(){
    console.log("首次渲染之前");
  }
  componentDidMount(){
    console.log("首次渲染之后");
  }
  componentWillUpdate(){
    console.log("将要更新");
  }
  componentDidUpdate(){
    console.log("更新完了");
  }
  <!--判断是否应该更新 -->
  shouldComponentUpdate(nextProps,nextState){
    if (nextState.num>5) {
      return false;
    }else {
      return true
    }
      }
  componentWillReceiveProps(nextProps){
      console.log('我的下一个props是',nextProps);
      if(nextProps.propsNum>5){
        alert('aaa')
      }
  }
  constructor(){
    super();
    this.state={
      num:0
  }
  }
  handleClick(){
    this.setState({num:this.state.num+1})
  }
  render () {
  return(
    <div>
    <p>{this.state.num}</p>
      <button onClick={this.handleClick.bind(this)}>click</button><br/>
    我的props是:
      {this.props.propsNum}
    </div>
  )
  }
}
```
### setInterval计时器

```js
class Timer extends Component {
  constructor(){
    super();
    this.state={
      second:0
    }
  }
  tick(){
    this.setState({second:this.state.second+1});
  }
  componentDidMount(){
    this.timer=setInterval(this.tick.bind(this),1000);
  }
  <!-- 每秒执行一次tick函数 -->
  shouldComponentUpdate(nextProps,nextState){
    console.log(nextState);
    if (nextState.second<10) {
      return true

    }else {
      clearInterval(this.timer);
      return true;
    }
  }
  render () {
    return(
      <div>
        <p>当前秒数为：{this.state.second}</p>
      </div>
    )

  }
}

```

# React Transform Boilerplate

## Installation

```bash
git clone https://github.com/gaearon/react-transform-boilerplate.git
cd react-transform-boilerplate
npm install
npm start
open http://localhost:3000
```

Transforms are enabled for files inside `src` (except `index.js`).
