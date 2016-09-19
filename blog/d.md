# 我是D页面--react 表单笔记


### 用h5方式做表单提交

```js
var TodoList = React.createClass({
  render: function() {
    var createItem = function(item) {
      return <li key={item.id}>{item.text}</li>;
    };
    return <ul>{this.props.items.map(createItem)}</ul>;
  }
});
var TodoApp = React.createClass({
  getInitialState: function() {
    return {items: [], text: ''};
  },
  onChange: function(e) {
    this.setState({text: e.target.value});
  },
  handleSubmit: function(e) {
    e.preventDefault();
    var nextItems = this.state.items.concat([{text: this.state.text, id: Date.now()}]);
    var nextText = '';
    this.setState({items: nextItems, text: nextText});
  },
  render: function() {
    return (
      <div>
        <h3>TODO</h3>
        <TodoList items={this.state.items} />
        <form onSubmit={this.handleSubmit}>
          <input onChange={this.onChange} value={this.state.text} />
          <button>{'Add #' + (this.state.items.length + 1)}</button>
        </form>
      </div>
    );
  }
});

ReactDOM.render(<TodoApp />, mountNode);
```
### react表单列表的提交
```js
class TodoList extends React.Component {
  constructor(){
    super();
    this.state={
      text:"",
      items:[]
    }
  }
  handleSubmit(e){
    e.preventDefault();
    this.state.items.push(this.state.text);
    //提交之后清空
    this.setState({text:''})
  }
  onChange1(e){
    this.setState({
      text:e.target.value
    })
  }
  render () {
  return(
    <div>
      <h3>TODO</h3>
      <ul>
    <!-- items数组的map遍历 -->
          {this.state.items.length==0 ? '请输入评论' : this.state.items.map((item,i)=> <li key={i}>{item}</li>)}
      </ul>
      <form onSubmit={this.handleSubmit.bind(this)}>
        <input onChange={this.onChange1.bind(this)} value={this.state.text} type="text"/>
        <button>add</button>
      </form>
    </div>
  )
  }
}

export default TodoList;
```
### react children属性

调用children属性
{this.props.children}
### browserHistory

browserHistory和hashHistory不一样，使用browserHistory的时候，浏览器中导航栏的URL就不会出现_k的hash键值对。实际项目中也一般用browserHistory.

```js
import React, { Component } from 'react';
import { Router, Route, browserHistory, Link } from 'react-router';

const Home = () => <div><h1>Home</h1><Links /></div>;
const About = () => <div><h1>About</h1><Links /></div>;
const Contact = () => <div><h1>Contact</h1><Links /></div>;

const Links = () =>
  <nav>
    <Link to="/">Home</Link>
    <Link to="/about">About</Link>
    <Link to="/contact">Contact</Link>
  </nav>

class App extends Component {
  render() {
    return (
      <Router history={browserHistory}>
        <Route path="/" component={Home} />
        <Route path="/about" component={About} />
        <Route path="/contact" component={Contact} />
      </Router>
    );
  }
}

export default App;
```
这样正常点击路由切换没有问题，但是重新刷新URL就会报找不到路由，这个时候我们在webpack-dev-server启动的时候需要加上参数--history-api-fallback。
### 简单路由配置

```js
import { Router, Route, browserHistory} from 'react-router';
import TodoList from './todoList';
import App from './App';
import About from './router'
ReactDOM.render(
  <Router history={browserHistory}>
      <Route path="/" component={App} />
      <Route path="/about" component={About} />
      <Route path="/list" component={TodoList} />
  </Router>
  , document.getElementById('app'));
```
### 用link做页面跳转

```js
import { Link } from 'react-router';
class App extends React.Component {
//Link l要大写 activeStyle为激活shift的样式
  render () {
  return(
    <div>
      111
      <Link to="/" activeStyle={{color:"red"}}>App</Link>
      <Link to="/about">About</Link>
      <Link to="/list">TodoList</Link>
    </div>
  )
  }
}

export default App;
```
### 路由嵌套

 ```js
 return(
    <Router history={browserHistory}>
        <Route path="/" component={App}>
            <Route path="/about:user " component={About} />
            /about:user--为动态路由
            <Route path="/list" component={TodoList} />
        </Route>
    </Router>
 )
 ```
