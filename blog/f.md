# 关于flex布局的运用
### flex教程

- webkit-font-smoothing: antialiased;反锯齿的，将字体变清晰
- display: flex;flex 布局
  - 设为Flex布局以后，子元素的float、clear和vertical-align属性将失效。
  - display: inline-flex;行内 flex 布局
  - display: -webkit-flex;Webkit内核的浏览器

### 容器属性

  - flex-direction：row | row-reverse | column | column-reverse; 属性决定主轴的方向（即项目的排列方向）。
  - flex-wrap：nowrap （不换行）| wrap （换行）| wrap-reverse（换行，第一行在下方）。;  flex-wrap属性定义，如果一条轴线排不下，如何换行。
  - flex-flow: <flex-direction> || <flex-wrap>;  flex-flow属性是flex-direction属性和flex-wrap属性的简写形式，默认值为row nowrap。
  - justify-content: flex-start | flex-end | center | space-between | space-around;
        属性定义了项目在主轴上的对齐方式。上下居中
        - flex-start（默认值）：左对齐
        - flex-end：右对齐
        - center： 居中
        - space-between：两端对齐，项目之间的间隔都相等。
        - space-around：每个项目两侧的间隔相等。所以，项目之间的间隔比项目与边框的间隔大一倍。
        - align-items: flex-start | flex-end | center | baseline | stretch;
        - flex-start：交叉轴的起点对齐。
        -  flex-end：交叉轴的终点对齐。
        -  center：交叉轴的中点对齐。
        -  baseline: 项目的第一行文字的基线对齐。
        -  stretch（默认值）：如果项目未设置高度或设为auto，将占满整个容器的高度。
  - align-content：flex-start | flex-end | center | space-between | space-around | stretch;
      align-content属性定义了多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用。
      - flex-start：与交叉轴的起点对齐。
      - flex-end：与交叉轴的终点对齐。
      - center：与交叉轴的中点对齐。
      - space-between：与交叉轴两端对齐，轴线之间的间隔平均分布。
      - space-around：每根轴线两侧的间隔都相等。所以，轴线之间的间隔比轴线与边框的间隔大一倍。
      - stretch（默认值）：轴线占满整个交叉轴。

### 项目属性
  - order  属性定义项目的排列顺序。数值越小，排列越靠前，默认为0。

  - flex-grow  属性定义项目的放大比例，默认为0，

  - flex-shrink  属性定义了项目的缩小比例，默认为1，

  - flex-basis  属性定义了在分配多余空间之前，项目占据的主轴空间（main size）。浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为auto，即项目的本来大小。

  - flex flex   该属性有两个快捷值：auto (1 1 auto) 和 none (0 0 auto)。属性是flex-grow, flex-shrink 和 flex-basis的简写，默认值为0 1 auto。后两个属性可选。

  - align-self align-self属性允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性。默认值为auto，         表示继承父元素的align-items属性，如果没有父元素，则等同于stretch。
    该属性可能取6个值，除了auto，其他都与align-items属性完全一致。

### 响应式覆盖属性

```css
@media (min-width:760px) {
  .content-warp{
    flex-direction: row;
  }

}
```

###  引入marked高亮样式
```js
import hljs from 'highlight.js';
import marked from 'marked';
```
