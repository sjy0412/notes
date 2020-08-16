1.font-size字体大小{
	px像素,最常用(普遍用14px,默认为16px)
	em相对于当前对象内文本的字体尺寸
	尽量用偶数的,可用多个字体用逗号隔开
}


2.font-family字体(宋体/微软雅黑/黑体等){
	font-family:"微软雅黑"
}


3.font-weight字体粗细{
	normal/bold/bolder/lighter
	100`900(100的整数倍)


4.font-weight:400等价于normal,700等价于bold
}


5.font-style:字体风格(normal/italic/oblique 正常/斜体/倾斜)


6.综合设置字体样式
	选择器{font:font-style font-weight font-size/line-height(行间隔) font-family;}
	不能更改顺序,不需设置的属性可省略(取默认),但必须保留font-size和font-family属性,不然不起作用


二、行高对齐
1.line-height设置行间距，一般比字号大7.8px左右
2.text-align设置文本内容水平对齐left right center
3.text-indent首行缩进，2em为两个汉字的宽度
4.leeter-spacing字间距，可用负值，默认为normal
5.word-spacing单词间距，对中文无用
6.颜色半透明 color：rgba（r，g，b，a）如color：rgba（0，0,0,0.2）
7.文字阴影text-shadow：水平位置 垂直位置 模糊距离 阴影颜色
如text-shadow：5px 11px 3px rgba（0,0,0,0.4）；前两个参数必须写

盒子阴影box-shadow 水平 垂直 阴影模糊程度 阴影缩放 阴影颜色
box-shadow:0px 0px 100px 0 blue inset; 默认影子在元素下面,加上inset后向内部蔓延

三、图片背景
background-color背景颜色
background-image:url(图片)
background-repeat是否平铺
background-position:left top左上角
background-position:bottom right右下角
background-position:center居中 如果方位名词只写一个,另一个默认为center
background-position:10px 30px精确单位,第一个为x坐标,第二个为y坐标
background-attachment:scroll背景图像随内容滚动
background-attachment:fixed背景图像固定

背景简写
background:背景颜色 背景图片地址 背景平铺 背景滚动 背景位置
background:blue url(images/lol.jpg) no-repeat fixed center 80px

背景半透明
background:rgba(0,0,0,0.5)

背景缩放
1.background-size:100px尽量只改一个值,防止缩放失真扭曲
2.background-size:50%缩放为原来一半
3.background-size:cover等比例缩放,会有部分超出看不见,常用
4.background-size:contain自动调整比例使图片始终完整显示在背景区域

多背景图片
background:url(images/l.jgp) no-repeat left top,
url(images/3.jpg) no-repeat bottom right pink;
为避免背景色将图像盖住,背景色通常定义在最后一组img



四、盒子模型
border盒子边框样式
border-width边框宽度|| border-style边框样式||border-color边框颜色
样式风格solid实线 ,dashed虚线,dotted点线,double双实线
综合写法border:1px solid bule;
border-top:1px solid green;
边框合并border-collapse:collapse;
圆角边框border-radius:左上角 右上角 右下角 左下角
border-radius:10px一个数值表示四个角都一样 取宽度的一半则是圆
div:nth-child(2)第二个
box-sizing: border-box; /*css3盒子模型border和padding都包含到width里面去*/

padding内容与边框之间的距离
margin外边距 
margin:auto 水平居中对齐  必须是块级元素且指定了宽度
.header{width:960px;margin:0 auto;}
margin:0清除外边距
padding:0清除内边距
*行内元素只有左右内外边距,没有上下内外边距

背景图片更改大小background-size
背景图片位置background-position
一般背景图片适合做一些小图标使用
产品类展示用插入图片,插入的图片也是一个盒子



解决父子之间外边距合并方法
1.为父元素定义1px的上边框或上内边距
2.为父元素添加overflow:hidden


浮动
添加浮动后,具有行内块元素特性:可以一行放多个,盒子大小由内容决定
子级里边一个浮动之后每个都要浮动

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

布局流程
1.确定页面的版心
2.分析页面中的行模块,以及每个行模块中的列模块
3.制作html页面,css文件
4.css初始化,然后开始运用盒子模型的原理,通过div+css布局来控制网页的各个模块
