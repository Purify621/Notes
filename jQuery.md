# jQuery

### 选择器

```javascript
1、标签选择器
$('标签')
例、
$('p').css('backgroundColor','pink')	//选择到p标签
2、类选择器
$('.类名')
$('.text').css('backgroundColor','pink')	//选择到类名为text的标签
3、id选择器
$('#id')
$('#text').css('backgroundColor','pink')	//选择到id为text的标签
4、后代选择器
$('标签 后代')
$('p a').css('backgroundColor','pink')	//选择到p下面的a标签
```

### jQuery事件绑定

```JavaScript
$('选择器').事件名(function(){
	//逻辑
})
例
$('li').click(function(){
     alert(1)
})
```

###  链式编程

```JavaScript
链式编程 通过点 ( . )	把多个操作方法连续的写下去，形成和链子一样的结构
$('.text').focus(回调函数).blur(回调函数).change(回调函数)
可以同时绑定多个事件，连续下去
示例、
$('input').focus(function(){
    console.log('获得焦点');  
})
.blur(function(){
    console.log('失去焦点')
})
```

### 内容操纵

```JavaScript
jQuery中封装了设置和读取网页元素文本内容的方法
语法、
设置		html方法解析标签，常用
$('选择器').html('内容')
$('选择器').text('内容')
读取		//不写内容就是读取
$('选择器').html()
$('选择器').text()
//设置时: html方法解析标签，text不解析
//取值时: html方法获取标签，text只获取文本
```

### 过滤方法

```JavaScript
//匹配第一个元素
.first()
//匹配最后一个元素
.last()
//根据索引匹配
.eq(索引)		//eq方法的索引从0开始
```

### 样式操纵

```javascript
1、键值对设置
.css('样式名','值')
.css('color','red')
.css('width','200px')
2、对象设置方式
.css(对象)
$('.box').css({
    backgroundColor:'pink',
    color:'red',
    width:'200px',
    height:'200'
})
3、样式取值
.css('样式名')
.css('width')
```

### 操作value

```JavaScript
1、赋值
.val('参数')
2、取值
.val.()
```

### 查找元素方法

```JavaScript
1、父元素
.parent()
2、子元素
.children()
3、兄弟元素
.siblings()
4、后代元素
.find('选择器')
//		findf方法需要传入选择器
//		children 、sibings方法支持传入选择器
```

### 获取到自定义属性

```JavaScript
例、
<div class="caption">
    <h3>销售额统计</h3>
    <a href="javascript:;" class="active" data-id="year">年</a>
    <a href="javascript:;" data-id="quarter">季</a>
    <a href="javascript:;" data-id="month">月</a>
</div>
//获取到自定义属性
$('.caption').on('click','a',function(){		//通过事件委托把点击事件绑定给a标签
    //a的自定义属性		this.dataset.id
    console.log(this.dataset.id)
})

dataset.自定义名		//自定义名是什么获取时后面就跟什么
例、
<a href="javascript:;" data-type="month">月</a>
this.dataset.type
```



### 操纵类名

```JavaScript
1、添加类名
.addClass('类名')
2、移除类名
.removeClass('类名')
3、判断类名，返回布尔值
.hasClass('类名')
4、切换类名
.toggleClass('类名')
```

### 事件进阶

```JavaScript
1、注册事件
.on('事件名',function(){})
2、移除指定事件
.off('事件名')
3、移除所有事件
.off()
4、注册一次性事件
.one('事件名',function(){})
//相关事件绑定都使用这种形式
$('对象').on('input',function(){
    
})
```

### 触发事件trigger

```JavaScript
通过代码的方式触发绑定的事件
1、直接触发
.事件名()
示例、
//直接触发
$('button').on('click',function(){
     $(this).css('background','skyblue')
})
$('button').click()		//代码会自己触发事件
2、trigger触发
.trigger('事件名')
示例、
$('button').trigger('click')
3、触发自定义事件('自定义事件')
.trigger('自定义事件')
4、注册自定义事件
.on('自定义事件',function(){})
```

### window事件绑定

```JavaScript
$(window).scroll(function(){	//滚动事件
})
$(window).click(function(){
})
```

### 获取位置

```JavaScript
1、取值
$('选择器').offset()
//取值
$('选择器').position()
//返回值
{top:126,left:58}
//参照物不同
offset参照html标签
position参照离他最近有定位的祖先元素
//margin
offset会把外边距margin计算进去
position以外边距margin为边界，不计算margin
```

### 滚动距离

```JavaScript
//取值
$('选择器').scrollLeft()
$('选择器').scrollTop()
//赋值
$('选择器').scrollLeft(值)
$('选择器').scrollTop(值)
```

### 显示和隐藏动画

```JavaScript
//显示
$('选择器').show(持续时间)		//单位是毫秒	1000毫秒是1秒
//隐藏
$('选择器').hide(持续时间)
//显示&隐藏
$('选择器').toggle(持续时间)
```

### 淡入淡出动画

```JavaScript
//淡入
$('选择器').fadeIn(持续时间)
//淡出
$('选择器').fadeOut(持续时间)
//淡入&淡出	切换
$('选择器').fadeToggle(持续时间)
```

### 展开收起动画

```JavaScript
展开(高度增大-显示)收起(高度减小-隐藏)
//展开
$('选择器').slideDown(持续时间)
//收起
$('选择器').slideUp(持续时间)
//展开&收起 切换
$('选择器').slideToggle(持续时间)
```

### 动画队列及停止方法

```JavaScript
//停止当前动画
$('选择器').stop()
//清空队列，在动画当前状态停止
$('选择器').stop(true)
//清空队列 直接到当前动画的结束状态
$('选择器').stop(true,true)
动画方法和stop方法返回的是一个jQuery对象

```

### 自定义动画

```JavaScript
$('选择器').animate(动画属性,持续时间)	//动画属性是以对象形式传入的
$('选择器').animate({
    width:100,
    height:100,
    margin:100
})
//注意
可支持多个
默认样式是px

//特殊属性
scrollTop
scrollLeft
//点击返回顶部
$('.gotop').click(function(){
   //点击之后让页面返回顶部
   $('html').animate({		//设置动画实现让返回顶部有动画效果缓慢回到顶部
     scrollTop:0
   },1000)
})
```

### 插入节点

```JavaScript
把元素插入/改变到父元素的里面
$('父元素选择器').append(参数) 	//父元素结尾
$('父元素选择器').prepend(参数)	//父元素开头
元素 插入/改变 到兄弟元素的身边
$('兄弟元素选择器').before(参数)	//兄弟元素前面
$('兄弟元素选择器').after(参数)	//兄弟元素后面
插入节点: 传入创建好的dom元素或者html结构
改变位置: 传入现有的dom元素或者jQuery对象
```

### 动画回调函数

```JavaScript
在所有动画属性后面都可以加回调函数
$('选择器').animate(属性,持续时间,回调函数)

1、回调函数设置的位置是最后一个参数
2、回调函数在动画执行完毕后执行
3、回调函数的this指的是播放动画的dom元素
```

### 延迟播放动画

```JavaScript
$('选择器').delay(延时时间).动画方法()		//单位都是毫秒
```

### 获取元素尺寸

```JavaScript
$('选择器').width()		//内容宽度
$('选择器').height()		//内容高度
$('选择器').innerWidth()		//内容宽度+内边距
$('选择器').innerHeight()		//内容高度+内边距
$('选择器').outerWidth()		//内容宽度+内边距+边框
$('选择器').outerHeight()		//内容高度+内边距+边框
$('选择器').outerWidth(true)		//内容宽度+内边距+边框+外边距
$('选择器').outerHeight(true)		//内容高度+内边距+边框+外边距
```

### 事件参数

```JavaScript
$('选择器').事件(function(e){		//用法和原生JavaScript一样
    e.stopPropagation()		//阻止冒泡
    e.preventDefault()		//阻止默认事件
})
```

### 删除节点

```JavaScript
jQuery对象.remove()
remove方法删除的是调用方法的元素节点		//谁调用删掉谁
```

### 事件委托

```JavaScript
事件委托是要绑定给父元素		写谁
$('父元素').on('事件名','后代选择器',function(){
    
})
减少事件注册
解决动态增加后代元素的事件绑定问题
回调函数的this是触发事件的dom对象

想委托给谁，就在后代选择器里
例如、
<ul class="todo-list" id="todoList">
    <li>
       <div class="view">
           <label>模板</label>
           <button class="destroy"></button>
        </div>
    </li>
</ul>
//此时就通过ul事件委托给	给类名为 .destroy 的button按钮绑定了点击事件
$('#todoList').on('click','.destroy',function(){
      let $li = $(this).parent().parent()   //找到小li
      $li.fadeOut(function(){   //动画删除
        $li.remove()
   })
})
```

### 入口函数

```JavaScript
1、入口函数作用是	页面资源加载完毕执行(包括图片，css等)
2、这样写可以把代码写到header部分	如果在头部引入js则需要把代码写到入口函数里面
jQuery写法
$(window).on('load',function(){		//会等待资源全部加载完毕执行
    
})
//ready写法
$(document).ready(function(){		//等dom加载完就执行
    
})
//简化写法		推荐
$(function(){})		//DOM载入完毕就执行
```

### 轮播插件 slick

```JavaScript
slick
//下载地址
https://github.com/kenwheeler/slick/

导入该插件要放到jQuery文件后
```

### 懒加载插件 lazyload

```JavaScript
懒加载 : 图片用到了在去加载，常用于有大量图片的网页，比如电商
导包
//先到jQuery
<script src="./js/jquery-3.5.1/jquery-3.5.1.min.js"></script>
//在到lzayload
<script src="./js/lazyload-2.x/lazyload.min.js"></script>
用包
<img class='lazyload' data-original="./image/1.png" alt="">
    把图片地址放到自定义属性 data-original=''里
    //找到希望懒加载的图片并调用lazyload方法
    $('lazyload').lazyload()

```

### 全屏滚动插件fullpage

```JavaScript
fullpage
//下载地址
https://alvarotrigo.com/fullPage/zh/
//引入相关css文件
<link rel="stylesheet" href="./JavaScript/fullPage.js-master/dist/fullpage.min.css">
//引入js文件
<script src="./JavaScript/fullPage.js-master/dist/fullpage.min.js"></script>
```

### 提交事件

```JavaScript
form标签本身具有提交数据的能力，但是基本不用

现在比较流行在表单的submit事件中阻止默认行为，自己获取数据并提交
$('form').submit(function(e){
    //阻止默认行为
    e.preventDefault()
    return false       //也能阻止默认行为
})
```

### 日期选择器插件datepicker

```JavaScript
首先
<!-- 导入日期选择器的样式 -->
<link rel="stylesheet" href="./datepicker/datepicker.css" />
    
<!-- 准备html结构 -->
<input type="text" class="datepicker" />
<!-- 导入jQuery -->
<script src="./jquery/jquery-3.5.1.js"></script>
<!-- 导入日期选择器插件 -->
<script src="./datepicker/datepicker.js"></script>
<!-- 导入语言包 -->
<script src="./datepicker/i18n/datepicker.zh-CN.js"></script>
   <script>
     $('.datepicker').datepicker({
       language: 'zh-CN',
       autoPick: true,		//是否自动选择当前日期
       autoHide: true,		//选择日期之后是否自动关闭
     })
</script>
```

### 表单验证插件validate

```JavaScript

```

### 克隆方法

```JavaScript
jQuery中封装了克隆(复制)，节点的方法
//不带事件
.clone()
//带事件
.clone(true)
方法返回的还是jQuery对象
传入ture会连事件一起拷贝
```

### jQuery转dom对象

```JavaScript
因为有些方法jQuery并没有完全封装，所以有些方法需要转回dom来使用
例、play(),pause(),reset()
//get方法获取
.get(索引)
//	[]
[索引]
示例、
<button class="play">播放</button>
<button class="pause">暂停</button>

let $btn = $('button')		//获取到所有的按钮	此时有两个
//get方法
$btn.get(1)		//获取到$btn里的第二个按钮
//[中括号]
$btn[0]		//获取到第一个按钮

```

### 表单序列化

```JavaScript
jQuery中封装了快速获取表单的value值，叫做序列化
$('form').serialize()
表单元素要有name属性才可以获取到value值
获取到的数据格式是	name1=value1 这种类型的字符串
```

### 插件机制

```JavaScript
拆建是jQuery提供的扩展机制，本质是往jQuery原型对象上添加方法
语法
jQuery.fn.extend({
    插件名(参数){
        //逻辑
    }
})
```



