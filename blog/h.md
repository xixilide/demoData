# React Transform Boilerplate

## echarts图表应用
[echarts](http://echarts.baidu.com/)网页

```js

import React from 'react';
import Echarts from 'echarts';

class App extends React.Component {


    componentDidMount(){
  let myChart = Echarts.init(document.getElementById('main'));
  myChart.setOption({
    title: { text: 'ECharts 入门示例' },
    tooltip: {},
    xAxis: {
        data: ["衬衫","羊毛衫","雪纺衫","裤子","高跟鞋","袜子"]
    },
    yAxis: {},
    series: [{
        name: '销量',
        type: 'bar',
        data: [5, 20, 36, 10, 10, 20]
    }]
});
    }
  render () {
    return(
      <div>
    <div id="main" style={{width: "600px",height:"400px"}}>
    </div>

    </div>
    )
  }
}

export default App;
```

### 轮播图

```js
import React from 'react';
import Echarts from 'echarts';
import Button from 'react-bootstrap/lib/Button';
import Carousel from 'react-bootstrap/lib/Carousel';
class App extends React.Component {

  render () {
    return(
      <div>
        <Carousel>
          <Carousel.Item>
            <img width={900} height={500} alt="900x500" src="http://7xopqp.com1.z0.glb.clouddn.com/contain-none.jpg"/>
            <Carousel.Caption>
              <h3>First slide label</h3>
              <p>Nulla vitae elit libero, a pharetra augue mollis interdum.</p>
            </Carousel.Caption>
          </Carousel.Item>
          <Carousel.Item>
            <img width={900} height={500} alt="900x500" src="http://7xopqp.com1.z0.glb.clouddn.com/contain-none.jpg"/>
            <Carousel.Caption>
              <h3>Second slide label</h3>
              <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
            </Carousel.Caption>
          </Carousel.Item>
          <Carousel.Item>
            <img width={900} height={500} alt="900x500" src="http://img2.3lian.com/2014/f3/4/d/58.jpg"/>
            <Carousel.Caption>
              <h3>Third slide label</h3>
              <p>Praesent commodo cursus magna, vel scelerisque nisl consectetur.</p>
            </Carousel.Caption>
          </Carousel.Item>
        </Carousel>
      </div>
    )
  }
}

export default App;
```
** 要引入样式
```js index.html文件中加
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/latest/css/bootstrap.min.css">

```
# material-ui用法

### 网上源代码
- app.js
```js
import React from 'react';
import RaisedButton from 'material-ui/RaisedButton';

const MyAwesomeReactComponent = () => (
  <RaisedButton label="Default" />
);

export default MyAwesomeReactComponent;
```
### 修改应用代码

```js
import React from 'react';

import RaisedButton from 'material-ui/RaisedButton';

import MuiThemeProvider from 'material-ui/styles/MuiThemeProvider';

class App extends React.Component {
  render () {
  return(
    <div>

      <MuiThemeProvider>
        <RaisedButton label="Default" />
      </MuiThemeProvider>
    </div>


  )
  }
}

export default App;
```
