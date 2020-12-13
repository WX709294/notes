## 如何实现左侧宽度固定，右侧宽度自适应的布局


https://juejin.cn/post/6844903928442667015#heading-7

- dom结构
```
  <div class="box">
    <div class="box-left"></div>
    <div class="box-right"></div>
  </div>
```
#### 利用$\color{red}{float + margin}$实现
```
  .box {
    height: 200px;
  }

  .box > div {
    height: 100%;
  }

  .box-left {
    width: 200px;
    float: left;
    background-color: blue;
  }

  .box-right {
    margin-left: 200px;
    background-color: red;
  }
```
#### 利用$\color{red}{calc}$计算宽度
```
  .box {
    height: 200px;
  }

  .box > div {
    height: 100%;
  }

  .box-left {
  width: 200px;
  float: left;
  background-color: blue;
}

.box-right {
  width: calc(100% - 200px);
  float: right;
  background-color: red;
} 
```
#### 利用$\color{red}{float + overflow}$计算宽度
```
  .box {
  height: 200px;
  }

  .box > div {
    height: 100%;
  }

  .box-left {
    width: 200px;
    float: left;
    background-color: blue;
  }

  .box-right {
    overflow: hidden;
    background-color: red;
  }
```

## 一般什么情况下会导致跨域
#### 跨域行为
  - 同源策略限制、安全性考虑
  - 协议、IP和端口不一致都是跨域行为
## 能说说首屏加载优化有哪些方案么
```
小提示：如果做过类似优化的同学，可能就比较好回答，没有做过类似优化的同学可以重点讲解一下懒加载（当然我这里被面试官追问过懒加载的Webpack配置问题）。同时不知道使用Vue技术栈的同学们有没有仔细观察过Vue CLI 3构建的html文件中的link标签的rel属性。
```
- Vue-Router路由懒加载（利用Webpack的代码切割）
- 使用CDN加速，将通用的库从vendor进行抽离
- Nginx的gzip压缩
- Vue异步组件
- 服务端渲染SSR
- 如果使用了一些UI库，采用按需加载
- Webpack开启gzip压缩
- 如果首屏为登录页，可以做成多入口
- Service Worker缓存文件处理
- 使用link标签的rel属性设置   prefetch（这段资源将会在未来某个导航或者功能要用
    到，但是本资源的下载顺序权重比较低，prefetch通常用于加速下一次导航）、preload（preload将会把资源得下载顺序权重提高，使得关键数据提前下载好，优化页面打开速度）
## Vue响应式原理 (必问)
  [基于Vue实现一个简易MVVM/数据劫持的实现](https://juejin.cn/post/6844904099704471559#heading-22)
## 伪类和伪元素的区别
  伪类和伪元素是用来修饰不在文档树中的部分，比如，一句话中的第一个字母，或者是列表中的第一个元素。下面分别对伪类和伪元素进行解释：

  伪类用于当已有元素处于的某个状态时，为其添加对应的样式，这个状态是根据用户行为而动态变化的。比如说，当用户悬停在指定的元素时，我们可以通过:hover来描述这个元素的状态。虽然它和普通的css类相似，可以为已有的元素添加样式，但是它只有处于dom树无法描述的状态下才能为元素添加样式，所以将其称为伪类。

  伪元素用于创建一些不在文档树中的元素，并为其添加样式。比如说，我们可以通过:before来在一个元素前增加一些文本，并为这些文本添加样式。虽然用户可以看到这些文本，但是这些文本实际上不在文档树中。

  #### 区别
  伪类的操作对象是文档树中已有的元素，而伪元素则创建了一个文档树外的元素。因此，伪类与伪元素的区别在于：有没有创建一个文档树之外的元素。

  CSS3规范中的要求使用双冒号(::)表示伪元素，以此来区分伪元素和伪类，比如::before和::after等伪元素使用双冒号(::)，:hover和:active等伪类使用单冒号(:)。除了一些低于IE8版本的浏览器外，大部分浏览器都支持伪元素的双冒号(::)表示方法。
