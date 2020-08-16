script基本步骤
1 获取元素
2 给按钮注册事件
3 控制事件要做的事
4 改变按钮中的文字

this的几种情况
1 普通函数中的this -> window
2 构造函数中的this -> 是当前构造函数创建的对象
3 方法中的this -> 方法所属的对象
4 事件处理函数中的this -> 事件源,谁调用的该事件this就指向谁


取消a的默认行为:直接在事件结尾加个return false

innerHTML innerText
innerHTML 获取内容的时候 如果内容中有标签会把标签页获取到 原封不动把内容取到
console.log(box.innerHTML);

innerText 获取内容的时候,如果内容中有标签会把标签过滤掉,把前后换行和空格都去掉
console.log(box.innerText);

设置标签之间的内容
box.innerHTML ='';//清空内容
如果内容中自带标签会以HTML的方式来解析
innerText设置内容,如果内容中带标签,在网页上会把标签显示出来

var array = [];
array.push(input.value);//把元素添加到数组中
array.join()//默认情况下逗号分割数组中的每一项
array.join('|');用|分割
