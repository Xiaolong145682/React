## 安装
* 首先需要下载React的安装包，可以从[官网](https://facebook.github.io/react/downloads.html)下载．
* hello world 入门例子
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>HTML-react</title>
  <script src="https://cdn.bootcss.com/react/15.6.1/react.js"></script>
  <script src="https://cdn.bootcss.com/react/15.6.1/react-dom.min.js"></script>
  <script src="https://cdn.bootcss.com/babel-core/5.8.38/browser.min.js"></script>
</head>
<body>
    <div id="example"></div>
    <script type="text/babel">
      ReactDOM.render(
        <h1>Hello, world!</h1>,
        document.getElementById('example')
      );
    </script>
</body>
</html>
```
* 注意：
    1. 首先`<script>`标签的`type`属性为`text/babel`.这是因为`React`独有的`JSX`语法，跟`javascript`不兼容．凡是要使用`JSX`的地方，都要加上`type = "text/babel"`.
    2. 前面引用了三个库文件，`react.js`是`react`的核心库文件；`react-dom.js`是提供与`DOM`相关的功能；`Browser.js`的作用是将`JSX`语法转为`Javascript`语法
## 核心思想
* 核心思想：封装组件，各个组件维护自己的状态和`UI`，当状态变更，自动重新渲染整个组件
* 好处：更改`UI`时，不再需要来回查找某个`DOM`元素
## 实现原理
* 原理：在Web开发中，我们总需要将变化的数据实时反应到UI上，这时就需要对DOM进行操作。而复杂或频繁的DOM操作通常是性能瓶颈产生的原因（如何进行高性能的复杂DOM操作通常是衡量一个前端开发人员技能的重要指标）。React为此引入了虚拟DOM（Virtual DOM）的机制：在浏览器端用Javascript实现了一套DOM API。基于React进行开发时所有的DOM构造都是通过虚拟DOM进行，每当数据变化时，React都会重新构建整个DOM树，然后React将当前整个DOM树和上一次的DOM树进行对比，得到DOM结构的区别，然后仅仅将需要变化的部分进行实际的浏览器DOM更新。而且React能够批处理虚拟DOM的刷新，在一个事件循环（Event Loop）内的两次数据变化会被合并，例如你连续的先将节点内容从A变成B，然后又从B变成A，React会认为UI不发生任何变化，而如果通过手动控制，这种逻辑通常是极其复杂的。尽管每一次都需要构造完整的虚拟DOM树，但是因为虚拟DOM是内存数据，性能是极高的，而对实际DOM进行操作的仅仅是Diff部分，因而能达到提高性能的目的。这样，在保证性能的同时，开发者将不再需要关注某个数据的变化如何更新到一个或多个具体的DOM元素，而只需要关心在任意一个数据状态下，整个界面是如何Render的
