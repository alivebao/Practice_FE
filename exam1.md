1. 如何实现一个三栏布局，要求两边固定宽度，中间自适应
用一个外框包裹三列，其position为relative，左右两列为absolut，中间设置对应margin即可
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
或者使用圣杯布局/双飞翼布局：
http://miaoyunze.com/2016/06/10/grail-flying-layout/
2. 说一下自己对 Javascript 变量提升的理解
答：不懂

3. 下面代码会打印什么？为什么?
答：打印一个空字符串，为什么？这里的this应该是window，打印结果应该是undefined啊？

4. setTimeout和setInterval的差别
执行setTimeout(xx, t),会在t秒后执行指定语句，
setInterval(xx, t)，系统会每隔t秒执行指定语句，改函数返回一个id，可通过clearInterval(id)取消该任务

5. 