# JavaScript-APIs

### 基本认知

DOM(文档对象模型)	BOM(浏览器对象模型)

### DOM对象

DOM是浏览器提供的一套专门用来操作网页内容的功能

```JavaScript
1、浏览器根据 html 标签生成的js 对象，所有的标签属性都可以在这个对象上面找到，修改这个对象的属性会自动映射到标签身上
2、DOM的核心就是把内容当对象来处理
例
标签
<button>点击</button>
当用js获取到button时，在js里是当对象来处理的	
在js里所有的标签都是对象
```

### DOM

#### 获取元素

##### querySelector 

```JavaScript
1、选择匹配的第一个元素
语法	document.querySelector('css选择器')
参数	包含一个或多个有效的css选择器 字符串
返回值	css选择器匹配的第一个元素，一个HTMLElement对象，如果没有则返回null
例、
<div>第一个div</div>
<div class="two">第二个div</div>
<ul>
        <Li>1</Li>
        <Li>2</Li>
        <Li>3</Li>
</ul>
let div = document.querySelector('div')		获取到第一个div，在有多个的情况下也是只获取到第一个
let div = document.querySelector('.two')	通过类名来获取到第二个div
let li = document.querySelector('ul li:last-child')		获取到最后一个li
('')里面写跟css一样的选择器，语法是一样的
```

##### querySelectorAll

```JavaScript
1、选择匹配的多个元素
语法	document.querySelectorAll('css选择器')
参数	包含一个或多个有效的css选择器 字符串
返回值	css选择器匹配的NodeList集合
例
<ul>
   <Li>1</Li>
   <Li>2</Li>
   <Li>3</Li>
</ul>
let div = document.querySelectorAll('ul li')	或取到ul下的所有li元素，会返回一个伪数组
   for(let i =0;i<div.length;i++){		//通过遍历来获取伪数组里的所有元素
      console.log(div[i])
   }
//	即使只获取一个元素querySelectorAll('')也会返回一个伪数组
```

其他获取DOM元素方法 ( 了解 ) 

```javascript
// 根据id获取一个元素
document.getElementById('#nav')
// 根据标签获取一类元素 获取页面所有div
document.getElementsByTagName('div') 
// 根据类名获取元素 获取页面 所有类名为 w 的元素
document.getElementsByClassName('w')
```

#### 修改元素

##### 常用属性

```JavaScript
元素.innerText属性
文本中包含的标签不会被解析
<div>
     pink
</div>
//获取元素
let div = document.querySelector('div')
//修改标签内容
//对象.属性 = 值
div.innerText = '有点意思'		//不能添加标签

元素.innerHTML属性		//建议使用
将文本内容添加 / 更新到任意标签位置
文本中的标签会被解析
div.innerHTML = '<strong>有点意思</strong>'	//可以添加标签，且标签会被解析

设置/修改元素常用属性
语法
对象.属性 = 值
例、
<img src="./images/1.webp" alt="">
//获取元素
let pic = document.querySelector('img')
//修改元素属性 src
pic.img = './images/2.webp'
pic.title = '我是'
```

##### 样式属性

```JavaScript
1、通过style属性操作css
语法
对象.style.样式属性 = 值
例
//获取对象
let box = document.querySelector('div')
//修改
box.style.background = 'pink'
//注意
1、修改样式通过style引出
2、如果属性有-连接符，需要转换为小驼峰命名法
3、赋值的时候，需要的时候不要忘记加css单位

2、通过类的方式操作css
使用于、如果修改的样式比较多，直接用style属性修改比较繁琐，我们可以借助于css类名的形式
语法
元素.className = 'active'
//注意，className是使用新值替换旧值，如果需要添加一个类，需要保留之前的类名
例、
.active{
    width:200px;
    height:200px;
}
<div class="one"></div>
js获取
let box = document.querySelector('div')
box.className = 'one active'	//要保留之前的类，必须把之前的类写上

3、通过classList操作控制css
//追加一个类
元素.classList.add('类名')
//删除一个类
元素.classList.remove('类名')
//切换一个类		当有这个类，则删除，没有这个类，则添加
元素.classList.toggle('类名')
//判断有没有包含某个类
元素.classList.contains('类名') 
例、
//1、获取元素
let box = document.querySelector('div')
//add是个方法 追加
box.classList.add('active')
//remove() 移除类
box.classList.remove('active')
//toggle() 切换类
box.classList.toggle('active')
```

##### 表单属性

```JavaScript
表单赋值/修改
获取	对象.属性名
修改	对象.属性名= 新值

value	可以取值或赋值

<input type="text" name="" value="11">
let input = document.querySelector('input')
取值
console.log(input.value);
赋值
input.value = '22'

属性
disable	不可用	当有该属性时表单不可用

let button = document.querySelector('button')
button.disabled=true	//设置为true时，则为可用

复选框
checked  为true时是选中状态	当为false时未选择
let check = document.querySelector('checked')
check.checked = true	//选中
check.checked = false	//未选中
```

#### 定时器-间歇函数

```JavaScript
setInterval(函数,间歇时间)
作用:每隔一段时间调用这个函数
间隔时间单位是毫秒
定时器返回的是一个数字，也就是当前定时器的编号
第一种定义方法
setInterval(function(){
     console.log('月薪过万');
},1000)
第二种定义方法
function show(){
    console.log('月薪过2万')
   }
setInterval(show,1000)		用这种方法时，函数名不需要加()

关闭定时器
let 变量名 = setInterval(函数,间隔时间)
clearInterval(变量名)		//删除定时器
```

### 事件基础

### 自动触发点击按钮

```javascript
元素已经绑定过点击事件才可用
元素.click()
```

事件监听

```JavaScript
元素.addEventListener('事件'，要执行的函数)
事件监听三要素
事件源:那个dom元素被事件触发了，要获取dom元素
事件:用什么方式触发，比如鼠标单击事件 click
事件调用的函数:要做什么事
示例
1、获取元素
let btn = document.querySelector('button')
2、添加事件监听
btn.addEventListener('click',function(){	//事件一定要加 ''
    alert('我被点击了')		//函数是点击之后才会执行，点击一次执行一次
}) 
```

##### 事件类型

```JavaScript
表单
获得焦点	focus
失去焦点	blur
//事件监听  获取光标事件 focus
input.addEventListener('focus',function(){
      //添加颜色类
      input.classList.add('search')
      //显示下拉菜单
      li.style.display = 'block'
})
//事件监听  失去光标事件 blur
input.addEventListener('blur',function(){
      //隐藏颜色类
      input.classList.remove('search')
      //隐藏下拉菜单
      li.style.display = 'none'
})

鼠标
经过	mouseenter	(推荐使用)	没有冒泡效果
离开	mouseleave	(推荐使用)	没有冒泡效果
鼠标移入
input.addEventListener('mouseenter',function(){
            
})
鼠标离开
input.addEventListener('mouseleave',function(){
            
})

键盘事件
按下	keydown		例、做拖拽时用到按下
松开	keyup

表单 input	只要出入就会触发
//1、获取到文本框
let area = document.querySelector('#area')
//2、绑定监听事件
area.addEventListener('input',function(){
	num.innerHTML = area.value.length	//动态获取到文本框里的value长度
}) 

change	当表单里面的值发生变化的时候触发和blur不一样	离开表单触发		//用于表单验证
input.addEventListener('change',function(){
	console.log(111)	//当表单里面的值发生变化时会打印111
}) 
```

### 高阶函数

```JavaScript
1、函数表达式
//函数表达式与普通函数本质上是没有区别的	
let counter = function(x,y){	//把函数当值来使用就是高阶函数
    return x+y
}
//调用函数
let result = counter(5,10)

2、回调函数	重点
如果将 函数A 作为参数传递给 函数B 时，我们称函数A为回调函数
例、
function fu(){}
setInterval(fn,1000)
//此时 fn就是回调函数	回头取调用的函数
//使用匿名函数做为回调函数比较常见
```

### 环境对象

环境对象指的是函数内部的特殊变量this，它代表着当前函数运行时所处的环境

```JavaScript
1、环境对象 this 它就是个对象
函数的调用方式不同， this 指代的对象也不同
[ 谁调用，this就是谁 ] 是判断 this 的粗略规则
例、
let btn = document.querySelector('button')
    btn.addEventListener('click',function(){
    console.log(this)
    //因为btn调用了这个函数，因此this就是btn
})
```

### 排它思想

当前元素为A状态，其它元素为B状态

使用

1、干掉所有人

​		使用for循环

2、复活他自己

​		通过this或者下标找到自己或者对应的元素

排他示例

```JavaScript
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
        .pink{
            background-color: pink;
        }
    </style>
  </head>
  <body>
    <button class="pink">点击1</button>
    <button>点击2</button>
    <button>点击3</button>
    <button>点击4</button>
    <button>点击5</button>
    <script>
      let btn = document.querySelectorAll("button");
      for (let i = 0; i < btn.length; i++) {
         btn[i].addEventListener('click',function(){
            /*1、先干掉所有人，把所有的样式都清除掉
            for(let j =0;j<btn.length;j++){
                btn[j].classList.remove('pink')
            }
            2、复活自己，在给自己设置样式
            this.classList.add('pink')
            */
             
            //1、新思想	(重点使用)
            //我们只需要找出那唯一的pink类，删除掉 querySelector方法只会找到其中唯一的那个，找到并删除
            document.querySelector('.pink').classList.remove('pink')
            //2、我的
            this.classList.add('pink')
         })
      }
    </script>
  </body>
</html>
```

### 节点操作

##### 查找节点

```javascript
节点关系

父节点查找
praentNode属性
返回最近一级的父节点
元素.praentNode属性
<div class="father">
    <div class="son">儿子</div>
</div>
let son = document.querySelector('.son')
//找爸爸
console.log(son.parentNode);

子节点查找
childNodes
获得所有的子节点，包括文本节点(空格，换行)
children(重点)
仅获得所有元素节点
返回的是一个伪数组
父元素.children
示例、
<button>点击</button>
    <ul>
      <li>我的孩子</li>
      <li>我的孩子</li>
      <li>我的孩子</li>
      <li>我的孩子</li>
      <li>我的孩子</li>
      <li>我的孩子</li>
    </ul>
<script>
   let btn = document.querySelector("button");
   let ul = document.querySelector("ul");
   btn.addEventListener("click", function () {
   //获取到所有的子节点是一个伪数组，通过遍历来获取所有子节点并改变样式
   for (let i = 0; i < ul.children.length; i++) {
          ul.children[i].style.color = "red";
   }
});
</script>

查找兄弟节点
1、下一个兄弟节点
nextElementSibling属性
2、上一个兄弟节点
previousElementSibling属性
```

##### 增加节点

```JavaScript
新增节点操作
1、创建一个新的节点
2、把创建的新节点放入到指定的元素内容 

1、创建元素节点方法
document.createElement('标签名')	//是一个方法
2、追加节点
2.1插入到父元素的最后一个子元素
父元素.appendChild(要插入的元素)
2.2插入到父元素中某个子元素的前面
父元素.insertBefore(要插入的元素,在那个元素前面)
//父元素
let ul = document.querySelector("ul");
//创建新的标签节点
let li = document.createElement('li')
li.innerHTML='我是追加的'
//追加节点，父元素.appendChild(子元素)	后面追加
ul.appendChild(li)
//追加节点，父元素.insertBefore(子元素,放到那个元素的前面)	指定追加到那个元素的前面
ul.insertBefore(li,ul.children[0])	//始终放到ul的子元素的第一个前面
```

##### 克隆节点

```JavaScript
1、克隆节点操作
复制一个原有的节点
把复制的节点放入到指定的元素内部
1.1
//克隆一个已有的元素节点
元素.cloneNode(布尔值)
cloneNode会克隆出一个跟原标签一样的元素，括号内传入布尔值
1、若为true，则代表克隆时会包含后代节点一起克隆
例、
<ul>
	<li>我的孩子</li>
</ul>
let ul = document.querySelector("ul");
let newUl = ul.cloneNode(true)	//此时会把ul的后代也克隆过来
/*克隆的结果为
<ul>
	<li>我的孩子</li>
</ul>
*/
2、若为false，则克隆时不包括后代节点
默认为false
<ul>
	<li>我的孩子</li>
</ul>
let ul = document.querySelector("ul");
let newUl = ul.cloneNode()	//不加任何值就是false	会只克隆当前
/*克隆的结果为
<ul>	</ul>
*/
```

##### 删除节点

```JavaScript
在JavaScript原生DOM中，要删除元素必须要通过父元素删除
语法
父元素.removeChild(要删除的元素)
/*注
删除节点和隐藏节点(dispaly:none)是有区别的，隐藏节点是还存在，但是删除，则从html中删除节点
*/
示例、
<button>点击删除</button>
<ul>
   <li>删除节点1</li>
   <li>删除节点2</li>
</ul>
<script>
   let btn = document.querySelector('button')
   let ul = document.querySelector('ul')
   btn.addEventListener('click',function(){
   //删除的语法 父元素.removeChild(子元素)
   ul.removeChild(ul.children[0])  //是ul下的第一个子节点
   })
</script>
```

### 时间对象

在代码中发现了new关键字时，一般将这个操作称为实例化

```javascript
1、获得当前时间
new 实例化 时间对象
//小括号为空能得到当前时间
let date = new Date()

2、获得指定时间
//小括号写时间能得到指定的时间
let date = new Date('2021-6-18 18:30:00')
```

##### 时间对象方法

```javascript
//使用方法，必须先实例化
let date = new Date()
date.getFullYear()	//获得年份
其它类似
```



| 方法          | 作用               | 说明                 |
| :------------ | ------------------ | -------------------- |
| getFullYear() | 获得年份           | 获得四位年份         |
| getMonth()    | 获得月份           | 取值位0~11           |
| getDate()     | 获取月份中的每一天 | 不同月份取值也不相同 |
| getDay()      | 获得星期           | 取值为0~6            |
| getHours()    | 获取小时           | 取值为0~23           |
| getMinutes()  | 获取分钟           | 取值为0~59           |
| getSeconds()  | 获取秒             | 取值为0~59           |

##### 时间戳

是总的毫秒数

计算倒计时: 核心思想

将来时间的毫秒数	- 	现在时间的毫秒数

转换为时分秒就是剩余的时间了

```JavaScript
三种方式获取时间戳
//	1、getTime()
let date = new Date()
consloe.log(date.getTime())

//	2、简写 +new Date()	推荐使用
console.log(+new Date())	//当前的时间戳
console.log(+new Date('2022-4-8 12:00:00'))	//指定的时间戳
//	3、Date.now()	只做了解
console.log(Date.now())
无需实例化	但是只能得到当前时间，而前面两种可以返回指定的时间戳

/*
注意:
1、通过时间戳得到的是毫秒数，需要转换为秒在计算
转换为秒数	(毫秒数) /1000 === 秒数
2、转换公式
d = parseInt(总秒数/60/60/24)	计算天数
h = parseInt(总秒数/60/60 % 24)	计算小时
m = parseInt(总秒数/60 % 60)	计算分数
s = parseInt(总秒数 % 60)	计算当前米秒数
*/
示例、计算指定时间到当前时间的时间差
//1、得到现在的时间戳
let now = +new Date();
//2、得到将来的时间戳
let last = +new Date("2022-4-8 12:00:00");
//3、(计算剩余的毫秒数) /1000 === 剩余的秒数
let count = (last - now) / 1000;
//4、转换为时分秒
let h = parseInt((count / 60 / 60) % 24);
let m = parseInt((count / 60) % 60);
let s = parseInt(count % 60);
```

##### 快速获取本地时间

```JavaScript
new Date().toLocaleString()
获取到年月日时分秒
```

### 重绘和回流

回流

当Render Tree 中部分或者全部元素的尺寸、结构、布局等发生改变时，浏览器就会重新渲染部分或全部文档的过程称为回流

简单理解，影响到布局了，就会有回流

重绘

由于节点(元素)的样式改变不会影响它在文档流中的位置和文档布局时(比如: color background-color outline 等) 称为回流

重点	重绘不一定引起回流，而回流一定引起重绘

### 事件高级

##### 事件对象

```javascript
事件对象就是一个对象，在事件监听的回调函数里
//在事件绑定的回调函数的第一个参数就是事件对象
//一般名为event、ev、e
元素.addEventListener('click',function(e){

})

//常用属性
1、type	获取当前的事件类型
2、clientX / clientY	获取光标相对于浏览器可见窗口左上角的位置
3、offsetX / offsetY	获取光标相对于当前DOM元素左上角的位置
4、用户按下的键盘键的值
e.key获取到当前按下键盘的值
例、
area.addEventListener('keyup',function(e){
      console.log(e.key)	//此时键盘按了什么键就能获取到，如果按了回车键，则会得到 'Enter' 按a 则会得到 a
})
5、pageX / pageY	跟文档坐标有关系	(用的较多)
```

##### 移除事件

```JavaScript
移除事件不能移除匿名函数，因此要把函数写到外面
window.addEventListener('click',fn)
function fn(){
	//要执行的函数
}
移除
window.removeEventListener('click',fn)
```

##### 事件流

事件流指的是事件完整执行过程中的流动路径

事件冒泡概念

```JavaScript
1、当一个元素的事件被触发时，同样的事件将会在该元素的所有祖先元素中依次被触发，这一过程被称为事件冒泡
2、简单理解、当一个元素触发事件后，会依次向上调用所有父级元素的同名事件
3、事件冒泡是默认存在的
let father = document.querySelector('.father')
let son = document.querySelector('.son')
father.addEventListener('click',function(){
      alert('我是爸爸')
})
son.addEventListener('click',function(){
      alert('我是儿子')
})
此时点击子元素，触发自己的alert后还会冒泡触发到父元素的电点击事件
简单理解先找儿子，在找爸爸
```

事件捕获的概念

```JavaScript
从DOM的根元素开始去执行对应的事件(从外到里)
事件捕获需要写对应代码才能看到效果
代码
DOM.addEventListener(事件类型,事件处理函数,是否使用捕获机制)
/*
addEventListener第三个参数传入true代表是捕获阶段触发(很少使用)
若传入false代表冒泡阶段触发，默认是false
若是用L0事件监听，则只有冒泡阶段，没有捕获
*/
let father = document.querySelector('.father')
let son = document.querySelector('.son')
father.addEventListener('click',function(){
      alert('我是爸爸')
},true)
son.addEventListener('click',function(){
      alert('我是儿子')
},true)
此时是先找爸爸，在找儿子
```

##### 阻止事件流动

```JavaScript
阻止事件流动需要拿到事件对象
语法
事件对象.stopPropagation()
此方法可用阻断事件流动传播

//阻止默认行为，比如链接点击不跳转
语法
e.perventDefault()
示例、
let a = document.querySelector('a')
a.addEventListener('click',function(e){
    //阻止a链接跳转	默认行为
    e.preventDefault()
})
```

##### 事件委托

事件委托是利用事件流的特征解决一些开发需求的知识技巧

使用场景	当需要给大量的绑定事件时

总结

优点: 给父级元素加事件(可以提高性能)

原理: 事件委托其实是利用事件冒泡的特点，给父元素添加事件，子元素可用触发

实现: 事件对象.target 可用获得真正触发事件的元素

```JavaScript
<ul>
   <li>我是第1个小li</li>
   <li>我是第2个小li</li>
   <li>我是第3个小li</li>
   <li>我是第4个小li</li>
   <li>我是第5个小li</li>
</ul>
<script>
    //不给每个小li添加事件了，而是把事件委托给它的爸爸
    //事件委托是给父元素添加事件，而不是给子元素添加事件
     let ul = document.querySelector('ul')
     ul.addEventListener('click',function(e){
         //得到当前的元素	e.target
         e.target.style.color='red'
     })
</script>
```

### 网页特效

##### 滚动事件

```JavaScript
当页面进行滚动时触发的事件
比如，固定导航栏，返回顶部
时间名: scroll

监听整个页面滚动
//页面滚动事件
window.addEventListener('scroll',function(){
    //执行的操作
})
给window 或 document 添加 scroll事件
监听某个元素的内部滚动直接给某个元素添加即可
```

##### 元素大小和位置

###### scroll家族

```JavaScript
使用场景
我们想要页面滚动一段距离，比如100px，就让某些元素显示隐藏，那么我们可用通过scroll来检测页面滚动的距离

1、获取宽高
获取元素的 内容 的总宽高(不包含滚动条)返回值不带单位
scrollWidth 和 scrollHeight
2、获取位置
获取元素内容往左，往上滚出去看不到的距离
scrollLeft 和 scrollTop
这两个属性是可以修改的

开发中、我们经常检测页面滚动的距离，比如页面滚动100px，就可用显示一个元素或则固定一个元素

window.addEventListener('scroll',function(){  
    //document.documentElement.scrollTop获得页面被卷去的头部
    console.log(document.documentElement.scrollTop)
    document.documentElement.scrollTop=500//属性是可用被修改的
})
//document.documentElement 获取的是HTML元素
```

###### offset家族

```JavaScript
1、使用场景
我想知道某个盒子到顶部的距离

2、获取宽高
获取元素自身的宽高、包含元素自身设置的宽高、包含padding、border
offsetWidth 和 offsetHeight
3、获取位置
获取元素距离自己 定位父级 元素的左、上距离
如果都没有父级则以 文档左上角为准
offsetLeft 和 offsetTop	//注意是只读属性
```

###### client家族

```JavaScript
当前可视区域
1、获取宽高
获取元素可见部分的高(不包含边框，滚动条等)
clientWidth 和 clientHeight
2、获取位置
获取左边框和上边框宽度
clientLeft 和 clientTop //只读属性	基本不用 了解即可
```

##### 加载事件

```JavaScript
加载外部资源 (如图片、外联css和JavaScript等) 加载完毕时触发的事件
1、使用场景
有时候需要等页面资源全部处理完了做一些事情

2、时间名: load
给window添加load事件
//页面加载事件
window.addEventListener('load',function(){
    //所有资源加载完毕在执行的操作
})
不光可用监听整个页面资源加载完毕，也可也针对某个资源绑定load事件

3、DOMContentLoaded
当初始的HTML文档被完全加载和解析完成之后，DOMContentLoaded被触发，而无需等待样式表、图像完全加载
监听页面DOM加载完毕
给 document 添加 DOMContentLoaded 事件
window.addEventListener('DOMContentLoaded',function(){
    //在执行的操作
})
```

### BOM

##### window对象

```html
window是浏览器内置中的全局对象，我们所学习的所有webAPIs 的知识内容都是基于window对象实现的
```

##### 定时器-延时函数

```JavaScript
JavaScript内置的一个让代码延迟执行的函数
setTimeout仅仅只执行一次，可用理解为就是把一段代码延迟执行
语法、
setTimeout(回调函数,等待的毫秒数)

let timer = setTimeout(回调函数,等待的毫秒数)
clearTimeout(timer)	//关闭定时器

//仅仅执行一次
setTimeout(function(){
     //隐藏元素
     console.log(1)
},3000)
//3秒后在控制台打印一次1 且只打印一次 
```

递归函数

```JavaScript
自己调用自己就是递归函数
 //利用递归函数 模拟了 setInterval
function fn(){
     div.innerHTML = new Date().toLocaleString()
     setTimeout(fn,1000) //每隔1秒，自己调用下自己
}
fn()
```

##### JavaScript执行机制

```JavaScript
1、JavaScript语言的一大特点就是单线程，也就是说，同一时间内只能做一件事
2、单线程意味着，所有的任务需要排队，前一个任务结束，才会执行后一个任务，如果有任务执行时间过长，会导致有页面加载慢的情况
3、同步和异步
为了解决这个问题，HTML5提出Web Worker标准，允许JavaScript脚本创建多个线程，也就是 同步和异步
4、同步
前一个任务结束后再执行后一个任务，程序执行顺序与任务排列顺序是一致的
5、异步
在做一件事的同时，也可以做其它事
6、同步任务
同步任务都在主线程上执行，形成一个执行栈
7、异步任务
JavaScript的异步是通过回调函数实现的
一般而言，异步任务有以下三种
7.1、普通事件	click resize
7.2、资源加载	lod	error
7.3、定时器		setInterval	setTimeout
异步任务放到任务队列中

//重点
执行机制
1、先执行执行栈中的同步任务
2、异步任务也放入任务队列中
3、一旦执行栈中所有的同步任务执行完毕，系统就会按次序读取任务队列中的异步任务，于是被读取的异步任务结束等待状态，进入执行栈，开始执行

事件循环(event loop)
1、主线程执行完毕，查询任务队列，取出一个任务，推入主线程处理
2、重复该动作
```

##### location

location 的数据类型是对象，它拆分并保存了url地址的各个组成部分

常用属性和方法

```JavaScript
1、href 属性获取完成的URL地址，对其赋值时用于地址的跳转
console.log(location.href)	//得到当前文件的URL地址
location.href = 'http://www.baidu.com'	//可以指定跳转到目标地址

2、search 属性获取地址中携带的参数，符号?后面的部分
//传递值的页面
<form action="target.html">
        <input type="text" name="username">
        <button>提交</button>
</form>
//接受值的页面
target.html
//完成的地址 location.href : http://127.0.0.1:5500/JavaScriptAPIs/day06/location-search.html
//是从上一个地址的表单里输入的值传递过来的
console.log(location.search)    //得到的是?username=123

3、hash 属性获取地址中的哈希值，符号#后面的部分
<a href='#one'></a>
console.log(location.hash)
//vue路由的铺垫，经常用于不刷新页面，显示不同页面，比如网易云音乐
4、reload 方法用来刷新当前页面，传入true时表示强制刷新
```

##### navigiator

```
navigator的数据类型是对象	该对象记录了浏览器自身的相关信息
```

##### history

```JavaScript
//了解即可
history的数据类型是对象，该对象与浏览器地址栏的操作相对应，如前进、后退、历史记录
//常用属性和方法
back()	//后退
forward()	//前进
go(参数)	//前进后退 1前进 -1后退
```

### swiper轮播插件

```JavaScript
https://www.swiper.com.cn/
```

### 本地存储(重要)

1、数据存储在用户浏览器中

2、设置、读取方便、甚至页面刷新不丢失数据

##### localStorage

声明周期永久有效，除非手动删除，否则关闭页面也会存在

可用多窗口(页面)共享(同一浏览器可以共享)

3、以键值对的形式存储使用

```JavaScript
存储数据
//存储数据  localStorage.setItem('键','值')
localStorage.setItem('uname','pink')
获取数据
//获取数据  localStorage.getItem('键')
console.log(localStorage.getItem('uname'))
```

##### 存储复杂数据类型

```JavaScript
本地只能存储字符串，无法存储复杂数据类型，需要将复杂数据类型转换为JSON字符串，在存储到本地
JSON.stringify(复杂数据类型)
将复杂数据类型转换为JSON字符串	存储本地存储中
JSON.parse(JSON字符串)
将JSON字符串转换为对象	取出时使用

示例
//1、存储复杂数据类型(引用数据类型)
let obj = {
     unmae:'pink',
     age:17,
     address:'黑马'
}
     //console.log(JSON.stringify(obj));
     //复杂数据类型一定要转换为JSON字符串在进行存储
     localStorage.setItem('obj',JSON.stringify(obj))
     //JSON 属性和值都是双引号包含
     /*
     let obj = {
         "unmae":"pink",
         "age":"17",
         "address":"黑马"
     }
     */
//取数据 可用使用    JSON.parse() 将JSON转换为字符串
console.log(JSON.parse(localStorage.getItem('obj')));
```

##### 自定义属性

```JavaScript
getAttribute('属性名')//获取自定义属性
setAttribute('属性名','属性值')//设置自定义属性
removeAttribute('属性名')//删除自定义属性

自定义属性	在标签上一律以 data-开头

当然除了在js里设置
也可以直接在HTML标签里写
<div class="box" data-index="0" data-id="1"></div>

在DOM对象上一律以dataset对象方式获取
console.log(box.dataset);//获取所有的自定义属性
console.log(box.dataset.index);	//获取指定的自定义属性
```

### 正则表达式

```JavaScript
是用于匹配字符串字符组合的模式
1、作用
表单验证(匹配)
过滤敏感词(替换)
字符串截取我们想要的部分(提取)
2、步骤
2.1、定义规则
2.2、查找 
```

##### 语法

```JavaScript
1、定义正则表达式语法
let 变量名 = /表达式/		/  /是正则表达式的字面量
比如
let reg = /前端/

2、判断是否有符合规则的字符串
test()方法 (重点)	用来查看正则表达式与指定的字符串是否相匹配
//示例
let reg = /前端/	
let str = '我们都在学前端'
console.log(reg.test(str));

3、检索
exec()方法	在一个指定字符串中执行一个搜索匹配，如果匹配成功则返回一个数组，否则为null
//示例
console.log(reg.exec(str));
```

##### 元字符

```JavaScript
是一些具有特殊含义的字符，可以极大提高了灵活性和强大的匹配功能
1、边界符(表示位置，开头和结尾，必须用什么开头，用什么结尾)
用来提示字符所在的位置，主要有两个字符
^	表示匹配行首的文本(以谁开始)
$	表示匹配行尾的文本(以谁结束)
如果^和$在一起，表示必须是精确匹配
// ^ 开头	以哈开头才为true
console.log(/^哈/.test('很哈'));    //false
console.log(/^哈/.test('哈哈'));    //true       
// $ 结尾	以哈结尾才为true
console.log(/哈$/.test('哈很'));    //false
console.log(/哈$/.test('很哈'));    //true   
// ^ $ 精确匹配
console.log(/^哈$/.test('哈哈'));    //false
console.log(/^哈$/.test('哈'));    //true

2、量词(表示重复次数)
用来设定某个模式出现的次数
*		重复零次或更多次	//量词 n>=0
+		重复一次或更多次	//量词 n>=1
?		重复零次或一次		//出现0||1
{n}		重复n次			//只能出现n次
{n,}	重复n次或更多次	//出现>=n次
{n.m}	重复n到m次			//出现n-m次
//注意:逗号左右两侧千万不要加空格

3、字符类(比如\d 表示0~9)
3.1、[] 匹配字符集合
3.2、[] 里面加上 - 连字符
使用连字符表示一个范围
例、
[a-z]	表示 a-z 26个英文字母都可以
[a-zA-Z]	表示大小写都可以
[0-9]	表示0~9的数字都可用
3.2、 [] 里面加上 ^ 取反符号
例、
[^a-z]	匹配除了小写字母以外的字符
//注意 要写到中括号里面
3.4、.匹配除了换行符之外的任何字符
3.5、字符类的预定义类
\d	匹配0-9之间的任一数字，相当于[0-9]
\D	匹配所有0-9以外的字符，相当于[^0-9]
\w	匹配任意的字母，数字和下划线，相当于[A-Za-z0-9_]
\W	除所有字母，数字和下划线，相当于[^A-Za-z0-9_]
```

##### 修饰符

```JavaScript
/表达式/修饰符
i	正则匹配时字母不区分大小写
g	匹配所有满足正则表达式的结果

替换 replace 替换
字符串.replace(/正则表达式/,'替换的文本')
常用来过滤敏感词
div.innerHTML = textarea.value.replace(/激情/g,'**')	//当textarea.value的值有 激情 两个字时会被替换为**
```

