### 基础类

* 如何实现一个三栏布局，要求两边固定宽度，中间自适应  
  答：用一个外框包裹三列，其position为relative，左右两列为absolut，中间设置对应margin即可
  ```javascript
  <div class="wrapper">
    <div class="left-50"></div>
    <div class="right-50"></div>
    <div class="center-auto"></div>
  </div>
  <style>
    .wrapper{
      height: 100%;
      width: 100%;
      min-width: 110px;
      position: relative;
    }
    .left-50,
    .center-auto,
    .right-50{
      height: 100%;
    }
    .left-50,
    .right-50{
      width: 50px;
      position: absolute;
    }
    .left-50{
      background: red;
      left: 0px;
    }
    .right-50{
      background: green;
      right: 0px;
    }
    .center-auto{
      margin: 0 50px;
    }
  </style>
  <div class="wrapper">
    <div class="left-50"></div>
    <div class="right-50"></div>
    <div class="center-auto"></div>
  </div>
  ```
  更多可参看我的博客 - 圣杯布局/双飞翼布局 - http://miaoyunze.com/2016/06/10/grail-flying-layout/  

* 说一下自己对 Javascript 变量提升的理解  
  答：没接触

* 下面代码会打印什么？为什么?  
  ```javascript
  <script>
    function A(){
      this.name = 'Daniel';
    }
    A.prototype.test = function(){
      setTimeout(function(){
        console.log(this.name);
      }, 1000);
    };
    var a = new A();
    a.test();
  </script>
  ```
  答：打印一个空字符串，为什么？这里的this应该是window，打印结果不应该是undefined吗？是否和上面说的变量提升有关？

* setTimeout和setInterval的差别  
  答：执行setTimeout(xx, t),会在t秒后执行指定语句  
  setInterval(xx, t)，系统会每隔t秒执行指定语句，该函数返回一个id，可通过clearInterval(id)取消该任务

* 如何实现类似jQuery的链式调用？  
  答：在函数执行完后返回自身即可。例：
  ```javascript
  <script>
    function A(){
      this.name = 'Daniel';
    }
    A.prototype.printA = function(){
      console.log("A");
      return this;
    }
    A.prototype.printB = function(){
      console.log("B");
      return this;
    };
    var a = new A();
    a.printA().printB().printA();
  </script>
  ```  

* Yslow 和 PageSpeed 你知道怎么用吗？你记得其中多少规则  
  答：没用过

* HTTP请求头中200/301/302/304分别代表什么？  
  答：
  * 200 - 服务器成功处理请求
  * 301 - 重定向(Permanently Moved)
  * 302 - 重定向(Temporarily Moved)
  * 304 - 服务器告诉客户原来缓存的文档还可以继续使用(节省服务器资源)  

* JPG和PNG的区别？  
  答：图片编码格式不同。
  * JPG - 有损压缩，较PNG而言图片质量一般，占空间小
  * PNG - 无损压缩，较JPN而言图片质量好，占空间大

* 事件冒泡和事件捕获有什么区别？  
  答：触发顺序不一样
  * 事件冒泡 - 最内层元素先触发
  * 事件捕获 - 最外层元素先触发

* 你遇到过兼容性问题吗？最令你印象深刻的兼容性问题是什么？  
  答：有两个
  * chrome autofill，input框会有黄色 - 具体可参看我的博客 - http://miaoyunze.com/2017/03/04/chrome-autofill/
  * DOM元素尺寸为小数的时候，IE有坑(滚动条) - key word - IE/小数/滚动条 - http://www.cnblogs.com/chuaWeb/p/5033273.html

### 工程类
  * 你使用过构建工具来编译前端代码吗  
    答：项目中使用grunt  

  * CDN是什么，原理？  
    答：内容分发网络，原理不清楚，它给我的感觉是 - 浏览器向服务器请求内容，服务器收到请求后根据当前环境选择合适的机器对该请求做出响应。  

  * 你使用过React、Vue、Angular其中之一吗？  
    答：项目中使用的是AngularJS 1.X， 自学过一段时间的React，翻译了React的官方文档(https://github.com/alivebao/React-Tutorial)    

  * 前端如何拿到DNS的查询时间  
    答：不知道  

  * 你能拿localStorage来做些什么  
    答：能实现在浏览器的多个tab页中共享sessionStorage。  
    在浏览器中的多个tab页中共享数据，可以通过cookie或localStorage实现。  
    某些情况下，需要在浏览器关闭后即清除该数据，可以通过sessionStorage完成。  
    但sessionStorage仅保存在当前tab页中，想要在多个tab中共享该数据，可通过localStorage实现。  
    具体可参看我的博客 - http://miaoyunze.com/2017/06/21/share-sessionData-between-tabs/  

  * 设计一个广告系统，类似广告联盟，如何对没有登录态的用户做跟踪？  
    答：对正常用户，用时间戳给访问的浏览器里设个cookie即可，操作简单可行性高，但只能绑定机器而不能绑定用户  
    对采用隐私模式的用户，尝试记录其ip，但ip是动态的，准确度低。  
    暂时没想到更好的方案。  