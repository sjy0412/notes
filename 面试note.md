js数组遍历
 	1.for循环
 		for(j=0,len=arr.length;j<len;j++){}

 	2.forEach()循环
	
	*3.map循环:map()中传入
	
	4.for..in循环可用于循环对象和数组
	
	let obj = {
		name: '王大锤',
		age:'18',
		weight:'70kg'
	}
	for(var key in obj){
		console.log(key);//name age weight 返回的是数组索引
		console.log(obj[key]);//王大锤 18 70kg
	}
    for...of 用于循环对象属性


##清除浮动
css浮动:浮动的元素会脱离正常的文档,在正常的文档流中不占用空间
    float属性: left  right
    流式布局
    clear属性:清除浮动
    both:两边都不允许浮动
    left:左边不允许浮动
    right:右边不允许浮动
清除浮动方法
1.在浮动元素末尾添加一个空标签如<div style="clear:both"></div>
2.父级添加overflow为hidden|auto|scroll触发BFC方式
3.使用after伪元素清除浮动
.clearfix:after{
	content:".";//内容为小点，不能空
	display:black;//转换为块级元素
	height:0;//高度为0
	clear:both;
	visibility:hidden;隐藏盒子
}
.clearfix{*zoom:1;}//*符号IE6、7专有
4.使用before和after双伪元素清除浮动(推荐使用)
.clearfix:before,.clearfix:after{
	content:"";
	display:table;
}
.clearfix:after{
	clear:both;
}
.clearfix{*zoom:1;}

选择器优先级
行内样式>id选择器>类选择器>元素选择器


无序列表u1
      li列表项
      ype:小圆圈circle,小方块square,默认小黑点disc
有序列表ol
      	常用属性:
      		type:指定序号类型
      		star:从几开始,必须写数字


盒子模型
每个盒子由四个部分组成,其效用由它们各自的边界所定义,
每个盒子四个边界,内容边界content Edge,内边距边界padding Edge
边框边界Border Edge,外框边界Margin Edge
padding-top是指一个元素在内边距区域中上方的高度


行内元素和块级元素的区别
块级元素会独占一行,默认情况下,其宽度自动填满其父元素宽度

块级元素可以设置width,height属性.
块级元素即使设置了宽度,仍然是独占一行.
块级元素可以设置margin和padding属性.
块级元素对应于display:block.
<h1>,<hr>,<p>,<ul>,<table表格>,<ul列表>,<form表单>,<div>等

*p,h1,dt等属于文字类块标签,不能放其他块级元素


行内元素不会独占一行,相邻的行内元素会排列在同一行里,直到一行排不下,才会换行

行内元素设置width,height属性无效，它的长度高度主要根据内容决定.

行内元素的margin和padding属性,水平方向的padding-left,padding-right,
margin-left,margin- right都产生边距效果,但竖直方向的padding-top,
padding-bottom,margin-top,margin-bottom却不会产生边距效果.
<span>,<a链接>,<br换行>,<b加粗>,<img图片>,<select下拉列表>等

*行内块元素:<img><input><td>可以设置宽高和对齐属性
display:inline块转行
display:block行转块
display:inline-block行内转行内块标签

网页从输入网址到渲染完成经历了哪些过程
发送到DNS服务器（解析），并获取域名对应的web服务器对应的ip地址；
与web服务器建立TCP连接（低级协议，高级协议基础）；
浏览器向web服务器发送http请求（高级协议）；
web服务器响应请求，并返回指定url的数据（或错误信息，或重定向的新的url地址）；
浏览器下载web服务器返回的数据及解析html源文件；
生成DOM树，解析css和js，渲染页面，直至显示完成


常见用户界面元素包括
1.用于插入url的地址栏
2.后退和前进按钮
3.书签选项
4.刷新和停止按钮以刷新或停止当前文档的加载
5.主页按钮,将您带到主页

作用域链
 内部环境可以通过作用域链来访问外部环境的属性和方法,但是外部环境不能访问内部环境的任何属性和方法.只能通过定义函数来延长作用域链条

闭包
 闭包就是能够读取其他函数内部变量的函数.由于在JavaScript语言中,主要函数内部的子函数才能读取局部变量,因此可以把闭包简单理解成"定义在一个函数内部的函数".最大的用处有两个, 可以读取函数内部变量;让这些变量的值始终保持在内存中

原型链


网页中引入的静态资源多了以后有什么问题?
 1. 网页加载速度慢,因为要发起多次的二次请求
 2. 要处理错综复杂的依赖关系

 解决方法:
  1 合并 压缩 精灵图 图片的Base64编码
  2 css放在head中; js放到body里最后的位置, 防止加载js阻塞页面
  3 静态资源使用多个域名 对应图片,css,js可以并发加载 
  4 使用离线缓存,把常用的变动少的js,css,图片存储到localstorage,第二次访问时直接走本地缓存


Vue双向绑定原理:
	采用数据劫持结合发布者-订阅者模式的方式
	通过object.defineProperty () 来重新获取get和设置set属性值


数组去重

1. 利用for嵌套for ,然后用数组的splice去重 
var data = [1,2,3,4,,5,1,1,2,3]
function unique(data) {
	for(var i= 0; i < data.length; i++) {
		for(var j = i+1; j < data.length; j++) {
			if(data[i] == data[j]) {
				data.splice(j, 1);
				j--; //因为去掉一个数之后,后一个下标就变成了去掉的数的下标,要-1
			}
		}
	}
	return data;
}

2. 建立新数组,利用indexOf去重
	function newArr(array) {
		var arrs = [];//一个新的空数组
		for(var i = 0; i < array.length; i++) {
			//如果临时数组里没有当前数组的当前值,则push到新数组中
			if(arrs.indexOf(array[i]) == -1) {
				arrs.push(array[i])
			};
		}
		return arrs;
	}

js内置对象,本地对象,宿主对象
本地对象（native object）为“独立于宿主环境的 ECMAScript 实现提供的对象
本地对象包含:(内部对象)
	Object Function Array String Boolean Number Date RegExp及各种错误类对象(Error EvalError RangeError ReferenceError SyntaxError TypeError URIError)
内置对象:
	独立于宿主环境的所有对象, 只有两个 Global Math (它们也是本地对象) 内置对象是本地对象的一种
宿主对象:
	浏览器提供的对象。所有的BOM和DOM都是宿主对象
	宿主对象就是执行JS脚本的环境提供的对象。对于嵌入到网页中的JS来说，其宿主对象就是浏览器提供的对象，所以又称为浏览器对象
浏览器对象有很多,如window和Document等

写一个通用的事件监听函数

