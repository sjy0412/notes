1 如何定义一个基本的vue代码结构
2 插值表达式 和 v-text
3 v-cloak 
4 v-html
5 v-bind vue提供的属性绑定机制 缩写是 : 
6 v-on vue提供的事件绑定机制 缩写是 @

注意: VM实例会监听自己身上data中所有数据的改变,只要数据一发生变化,就会自动 把最新的数据从data上同步到页面中去;[好处:程序员只需要关心数据,不需要考虑如何重新渲染DOM页面]

*注意:在vm实例中,如果想要获取data上的数据,或者想要调用methods中的方法,必须通过 this.数据属性名 或 this.方法名来进行访问,这里的this 就表示我们 new 出来的 vm实例对象

事件修饰符 
.stop 阻止冒泡
.prevent 阻止默认行为
.capture 实现捕获触发事件的机制
.self 实现只有点击当前元素时候才会触发事件处理函数
.once 只触发一次事件处理函数
v-bind 只能实现数据的单向绑定,从M自动绑定到V,无法实现数据的双向绑定 
v-model 指令可以实现表单元素和 model 中数据的双向数据绑定 
v-model只能运用在表单元素中 //input(radio,text,address,email...) select checkbox textarea

v-for 循环的时候, key 属性只能使用number获取string 
key在使用时,必须使用v-bind属性绑定的形式,指定key的值 
在组件中,使用v-for循环的时候,或者在一些特殊情况中,如果v-for有问题 必须在使用v-for的同时,指定唯一的字符串/数字类型 :key值

v-if:每次都会重新删除或者创建元素 
v-show:每次不会重新进行DOM的删除和创建操作,只是切换了元素的display:none样式 
v-if 有较高的切换性能消耗 v-show 有较高的初始渲染消耗 
如果元素涉及到频繁的切换,最好不要使用v-if 
如果元素可能永远也不会被显示出来被用户看到,则推荐使用v-if

在vue中绑定样式的两种方式: v-bind:class v-bind:style

vue组件
1.1 使用vue.extend来创建全局的vue组件
1.2使用 vue.component('组件的名称', 创建出来的组件模板对象)
    使用Vue.component 定义全局组件的时候,组件名称使用了驼峰命名,则在引用组件的时候,需要把大写的驼峰改为小写的字母,同时两个单词之间 ,使用 - 链接
    如果不使用驼峰,则直接拿名称来使用即可
    如果要使用组件,直接把组件的名称以HTML 标签的形式,引入到页面中即可

组件传值
1. 父传子 通过props属性,该属性定义在子组件中
2. 子组件给父组件传值是通过$emit方法
3. 路由带参数进行传值

vue-router路由   (实现组件的切换)
路由匹配过程:
 1 点击对应的超链接 (会修改url地址)
 2 修改url地址之后,路由对象注册到vm身上,然后路由会监听到url地址的改变,于是进行路由规则的匹配 看有没有匹配到的path ,如果匹配到就会展示到<router-view></router-view>中

 路由基本使用:
  1 导入包<script src="../lib/vue-router v3.4.1.js"></script>
  2 创建路由组件
  3 创建路由对象
  4 将路由规则对象, 注册到 vm 实例上,用来监听 URL 地址的变化 ,然后展示对应的组件
  5 在页面写一个容器<router-view></router-view>
    标签 <router-link to="/login" tag="span">登录</router-link>

watch computed methods 对比
1.computed 属性结果会被缓存,除非依赖的响应式属性变化才会重新计算,主要当做属性来使用
 (当数据需要经过一系列处理时使用computed)
2.methods方法表示一个具体的操作,主要书写业务逻辑
3,watch 一个对象,键是需要观察的表达式,值是对应回调函数.主要用来监听某些特定数据的变化,从而进行某些具体的业务逻辑操作
(watch主要用来监听虚拟的)