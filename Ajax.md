# Ajax

### 什么是Ajax

```JavaScript
在网页中利用XML HttpRequest 对象和服务器进行数据交互的方式就Ajax
```

### URL地址的组成部分

1、客户端与服务器之间的	**通信协议**
2、存有该资源的	**服务器名称**
3、资源在服务器上	**具体存放的位置**

```javascript
http://www.cnblogs,com/liiulongbinblogs/p/11649393.html
1、http://	是通信协议
2、www.cnblogs,com/	是服务器名称
3、liiulongbinblogs/p/11649393.html	资源在服务器上具体的位置
```

### 资源的请求方式

```JavaScript
客户端请求服务器时，请求的方式有很多种，最常见的两种方式为get 和 post 请求
1、get 请求通常用于获取服务器资源(向服务器要资源)
2、post 请求通常用于向服务器提交数据(往服务器发送数据)
```

### jQuery中的Ajax

```JavaScript
jQuery中发起Ajax请求最常用的三个方法如下
$.get()
$.post()
$.ajax( )
```

### $.get()函数

```JavaScript
$.get()函数、专门用来发起get请求，从而将服务器上的资源请求到客户端来进行使用

1、$.get()语法
$.get(url,[data],[callback])		//[]是可选参数
```

| 参数名   | 参数类型 | 是否必选 | 说明                     |
| -------- | -------- | -------- | ------------------------ |
| URL      | string   | 是       | 要请求的资源地址         |
| data     | object   | 否       | 请求资源期间要携带的参数 |
| callback | function | 否       | 请求成功时的回调函数     |

##### $.get()发起不带参数的请求

```JavaScript
$.get('http://www.liulongbin.top:3006/api/getbooks',function(res){
            console.log(res);       //服务器返回的数据
})
```

##### $.get()发起带参数的请求

```JavaScript
$.get('http://www.liulongbin.top:3006/api/getbooks',{id:1},function(res){
     console.log(res);       //服务器返回的数据
})
```

### $.post()函数

```JavaScript
$.post()函数、专门用来发起post请求，从而向服务器提交数据

1、$.post()语法
$.post(url,[data],[callback])
```

| 参数名   | 参数类型 | 是否必选 | 说明                     |
| -------- | -------- | -------- | ------------------------ |
| URL      | string   | 是       | 提交数据的地址           |
| data     | object   | 否       | 要提交的数据             |
| callback | function | 否       | 数据提交成功时的回调函数 |

##### $.post()向服务器提交数据

```JavaScript
$.post(      
    "http://www.liulongbin.top:3006/api/addbook",     //请求的url地址
    { bookname: "水", author: "施", publisher: "上海" },  //提交的数据
    function (res) {      //回调函数
         console.log(res);       
    }
);
```

### $.ajax()函数

```JavaScript
$.ajax()函数，功能比较综合，它允许我们对Ajax请求进行更详细的配置
$.ajax({
    type:'',	//请求的方式 GET 或 POST
    url:'',		//请求的url地址
    data:{},	//这次请求要携带的数据
    success: functuion(res){}	//请求成功之后的回调函数
})
```

##### $.ajax()发起GET请求

```JavaScript
$.ajax({
    type:'get',		//请求的方式
    url:'http://www.liulongbin.top:3006/api/getbooks',		//请求的url地址
    data:{id:1},	//这次请求要携带的参数，如果没有则可以省略
    success:function(res){		//请求成功之后的回调函数
        console.log(res)
    }
})
```

##### $.ajax()发起POST请求

```JavaScript
$.ajax({
     type:'post',		//请求的方式
     url:'http://www.liulongbin.top:3006/api/addbook',		//请求的url地址
     data:{		//要提交给服务器的数据
          bookname:'水浒传',
          author:'施耐庵',
          publisher:'上海图书出版社'
     },
     success:function(res){		//请求成功之后的回调函数
          console.log(res)
     }
})
```

### 接口

```
使用Ajax请求数据的时候，被请求的URL地址，就叫做数据接口 (简称 接口) ，同时，每个接口必须有请求方式
例、
http://www.liulongbin.top:3006/api/getbooks		获取图书列表的接口(GET请求)
http://www.liulongbin.top:3006/api/addbook		添加图书的接口(POST接口)
```

接口文档

```JavaScript
1、什么是接口文档
接口文档就是接口的说明文档，它是我们调用接口的依据，我们参照接口文档就能方便知道接口的作用
2、接口文档的组成部分
接口名称: 用来标识各个接口的简单说明
接口URL: 接口的调用地址
接口的调用方式: 接口的调用方式，GET或POST
参数格式: 接口需要传递的参数 每个参数必须包含 参数名称、参数类型、是否必选、参数说明这4项内容
响应格式: 接口的返回值的详细描述，一般包含数据名称，数据类型，说明
```

### form表单与模板引擎

#### 组成部分

```JavaScript
<form action="">
    <input type="text" name="" id="">
    <input type="password" name="" id="">
    <input type="checkbox" name="" id="">
    <button>提交</button>
</form>
表单由三个部分组成
1、表单标签
2、表单域	//表单域包含: 文本框，密码框，隐藏域，多行文本框，复选框，单选框，下拉选择框，和文件上传框
3、表单按钮
```

#### form表单的属性

form标签用来采集数据，	form标签的属性则是用来规定如何把采集到的数据发送到服务器

```JavaScript
1、action
action 属性用来规定当提交表单时，向何处发送数据
action 属性的值应该是后端提供的一个URL地址，这个地址专门用来接收表单提交过来的数据
当未指定数据时，则会提交到当前页面
//注意 当提交表单后，页面会立即跳转到action属性指定的URL地址

2、target
target 属性用来规定在何处打开 action URL
它的可选值有5个，默认情况下，target的值是 _self,标识在相同的框架打开 action URL
//其它值
_blank		在新窗口打开
_self		默认，在相同的框架打开
_parent		在父框架集中打开(很少用)
_top		在整个窗口打开(很少用)
frmename	在指定的框架打开(很少用)

3、method
method 属性用来规定以何种方式把表单数据提交到action URL
它的值有两个为 get 和 post
默认情况下 method的值为get 
//注意
get 方式适合提交少量的简单的数据
post 方式适合用来提交大量的、复杂的，包含文件上传的数据
// 在实际开发中 post提交方式用的最多

4、enctype
enctype 属性用来规定在发送表单数据之前如何对数据进行编码
它的可选值有三给，默认情况下，enctype的值为 application/x-www-form-urlencoded，表示在发送前编码所有的字符
//其它值
multipart/form-data		不对字符进行编码，在使用包含文件上传空间的表单时，必须使用该值
text/plain		空格转换为 + 号，但不对特殊字符进行编码(很少用)
//注意，当使用文件上传的操作时，必须将 enctype 的值设置为multipart/form-data
```

#### 解决表单同步提交的缺点

```JavaScript
表单同步提交有两个缺点，会导致两个问题
1、页面会发生跳转
2、页面之前的状态会丢失

// 解决
表单只负责采集数据，Ajax负责将数据提交到服务器
```

### 通过Ajax提交表单数据

#### 监听表单提交事件

```JavaScript
jQuery有两种监听的方式
1、第一种
$('#form1').submit(function(e){
     alert('监听到了表单的提交事件')
})
2、第二种
$('#form1').on('submit',function(e){
     alert('监听到了表单的提交事件')
})
```

#### 阻止表单的默认提交行为

```JavaScript
1、当监听到表单的提交事件以后，可以调用事件对象的 e.preventDefault() 函数，来阻止表单的提交和页面的跳转
2、实例代码、
$('#form1').submit(function(e){
     e.preventDefault()
})

$('#form1').on('submit',function(e){
     e.preventDefault()
})
```

#### 快速获取表单的数据

```JavaScript
1、serialize()函数
语法、
$(selector).serialize()
好处是可以一次性获取到表单中的所有的数据
//注意	在使用serialize()函数快速获取表单数据时，必须为每个表单元素添加name属性
2、实例
<form id="form1" action="">
    <input type="text" name="name" id="">
    <input type="password" name="password" id="">
    <button>点击</button>
</form>
$('#form1').on('submit',function(e){
     e.preventDefault()		//阻止默认提交行为
     $('#form1').serialize()
     //调用的结果	name = 用户名的值 & password = 密码的值
     console.log($('#form1').serialize());		
})
```

### 模板引擎

```
模板引擎，根据程序员指定的模板结构和数据，自动生成一个完整的HTML页面
```

#### art-template模板引擎

```JavaScript
使用步骤
1、导入
2、定义数据
3、定义模板
4、调用 template函数
5、渲染HTML结构
```

```JavaScript
模板示例、
<!-- 1、导入模板引擎   在window全局中多一个函数 template('模板的id','需要渲染的数据对象') -->
<script src="./js/template-web.js"></script>
<script src="./js/jquery-3.5.1.min.js"></script>

<div id="common"></div>

<!-- 3、 定义模板 -->
<!-- 模板的HTML结构必须放到 script标签里面  如果script不指定type属性的话，默认是 text/JavaScript
    但是不能渲染html结构，因此我们要改为 type="text/html"
    {{}}   是html的占位符  
-->
<script type="text/html" id="con">
    <h1>{{name}}  ---  {{age}}</h1>
</script>
<script>
    // 2、定义数据
    let data ={name:'谢',age:21}
    //4、调用template函数
    let com = template('con',data)
    //5、渲染到页面上
    $('#common').html(com)
</script>

```

#### 标准语法

```javascript
art-template 提供了{{ }} 这种语法格式
在{{ }}内可以进行变量输出，或循环数组等操作，这种{{ }}语法在art-template中被称为标准语法
在{{ }} 里，可以进行变量的输出，对象属性的输出，三元表达式输出，逻辑或输出，加减乘除等表达式输出
例、输出
{{value}}
{{obj.key}}
{{obj['ket]}}
{{a?b:C}}
{{a||b}}
{{a+b}}
```

##### 标准语法-原文输出

```
{{@ value}}
如果要输出的value值中，包含了HTML结构，则需要使用原文输出语法，才能保证HTML结构被正常渲染
```

##### 标准语法-条件输出

```JavaScript
如果要实现条件输出，则可以在{{ }}中使用if  else if  /if的方式按需进行输出
1、一种判断
{{if value}} 按需输出的内容 {{/if}}
如果if为真则执行后面的内容
2、多种判断
{{if v1}} 按需输出的内容 {{else if v2}} 按需输出的内容{{/if}}
匹配到那个则输出到那个后面的内容
```

##### 标准语法-循环输出

```JavaScript
如果要实现循环输出，则可以在{{ }}内，通过each语法循环数组，当前循环数组索引使用$index进行访问，当前的循环项用$value进行访问
{{each arr}}
	{{$index}}//数组的索引值	{{$value}}//数组的值
{{/each}}
```

##### 标准语法-过滤器

```JavaScript
{{value | filterName}}		//  |左边是值、右边是处理函数
过滤器的语法类似管道操作符，它的上一个输出会作为下一个输入

定义过滤器的基本语法
template.defaults.imports.filterName = function(value){/*return 处理的结果*/}

示例、
<h3>{{regTime | dateFormat}}</h3>
let data ={name:'谢',age:21, regTime: new Date()}
//定义时间过滤器
template.defaults.imports.dateFormat = function(date){
     let y = date.getFullYear()
     let m = date.getMonth() +1
     let d = date.getDate()
     return y+'-'+m+'-'+d		//过滤器最后必须return一个值
} 
```

### 模板引擎的实现原理

#### 正则与字符串操作

##### 基本语法

```JavaScript
1、基本语法
exec()函数 用于检索字符串中的正则表达式的匹配
如果字符串中有匹配的值，则返回该匹配的值，否则返回null
示例、
let str = 'hallo'
let pattern = /o/
console.log( pattern.exec(str) )
//输出的结果 ['0',index:4,'hello',groups:undefined]
```

##### 分组

```JavaScript
2、分组
在正则表达式中()是一个分组，可以通过分组来提取自己想要的内容
let str = "<div>我是{{name}}</div>"
let parsent = /{{ ([a-zA-Z]+) }}/		//通过()来提取内容
let resurt = parsent.exec(str)
console.log(resurt)
//得到name的分组信息
['{{name}}', 'name', index: 7, input: '<div>我是{{name}}</div>', groups: undefined]
```

##### replace函数

```JavaScript
3、replace函数
replace()函数用于在字符串中用一些字符串替换另外一些字符串
let str = "<div>我是{{name}}</div>"
let parsent = /{{([a-zA-Z]+)}}/
let resurt = parsent.exec(str)
str = str.replace(resurt[0],resurt[1])		//把resurt数组的0替换为1
console.log(str)

4、多次replace操作
<script>
      //字符串的多次匹配操作
      let str = '<div>我叫{{name}}今年{{ age }}岁了</div>'
      let pattern = /{{\s*([a-zA-Z]+)\s*}}/
      //第一次提取
      let res1 = pattern.exec(str)
      str = str.replace(res1[0],res1[1])
      console.log(str)
      //<div>我叫name今年{{ age }}岁了</div>

      //第二次提取
      let res2 = pattern.exec(str)
      str = str.replace(res2[0],res2[1])
      console.log(str)
      //<div>我叫name今年age岁了</div>

      //第三次提取  当字符里没有可以匹配的内容时会返回null
      let res3 = pattern.exec(str)
      console.log(res3)
      //null
</script>
```

##### 使用while循环replace函数

```JavaScript
//通过循环把值替换为真值
let data = {name:'pink',age:23}
let str = '<div>我叫{{name}}今年{{ age }}岁了</div>'
let pattern = /{{\s*([a-zA-Z]+)\s*}}/
let patternResult = null
while(patternResult = pattern.exec(str)){   //当没有匹配结果时会返回null则会退出循环
	str = str.replace(patternResult[0], data[patternResult[1]] )		//date的取值由patternResult[1]来决定
}
console.log(str)
//<div>我叫pink今年23岁了</div>
```

# Ajax加强

### xhr基本使用

#### 使用xhr发起GET请求

```JavaScript
//1、创建对象
let xhr = new XMLHttpRequest()
//2、调用open函数
xhr.open('GET','http://www.liulongbin.top:3006/api/getbooks')
//3、发起send请求
xhr.send()
//4、监听
xhr.onreadystatechange = function(){
// 判断条件是固定写法   此时判断的 status 与获取到的 status 不是同一个值
	if(xhr.readyState ===4 && xhr.status === 200){
        //获取到响应的数据
     	console.log(xhr.responseText);
     }
}

发起带参数的GET请求	只需在调用xhr.open期间，为url指定地址即可
xhr.open('GET','http://www.liulongbin.top:3006/api/getbooks?id=1')
id=1 就是要传递的参数	这种在url地址后面拼接的参数，叫做查询字符串
```

#### GET请求携带参数的本质

```JavaScript
无论是使用$.ajax(),还是使用$.get(),又或者直接使用xhr对象发起GET请求，当需要携带参数的时候，本质上都是直接将参数以查询字符串的形式，追加到URL地址的后面，发送到服务器的
```

#### 使用xhr发起POST请求

```JavaScript
//1、创建xhr对象
let xhr = new XMLHttpRequest()
//2、调用open函数
xhr.open('POST','http://www.liulongbin.top:3006/api/addbook')
//3、设置Content-type属性   (固定写法)
xhr.setRequestHeader('Content-type','application/x-www-form-urlencoded')
//4、调用send函数
xhr.send('bookname=水浒传&author=施耐庵&publisher=上海图书出版社')
//5、监听事件
xhr.onreadystatechange = function(){
    if(xhr.readyState === 4 && xhr.status === 200){
        console.log(xhr.responseText)
    }
}
```

#### 了解xhr的readyState属性

```JavaScript
XMLHttpRequest对象的 readyStatue 属性，用来表示当前Ajax请求所处的状态
0	XMLHttpRequest已经被创建，但未调用open方法
1	open()方法已被调用
2	send()方法已被调用，响应头也已经被接受
3	数据接受中，此时response属性以及包含部分数据
4	Ajax请求完成，这意味着数据传输彻底完成或失败
```

#### 了解查询字符串

```JavaScript
查询字符串指的是在url的末尾加上用于向服务器发送信息的字符串
格式、
将英文的 ? 放在URL的末尾，然后在加上 参数=值 ，想加多给值的话用 & 符号进行分隔
```

#### URL编码

```JavaScript
URL地址中，只允许出现英文相关的字母，标点符号，数字，因此在URL地址中不允许出现中文字符
如果需要包含中文这样的字符，需要对字符进行编码
URL编码: 使用英文字符去表示非英文字符
http://www.liulongbin.top:3006/api/getbooks?id=1&bookname=西游记
经过编码后变为了
http://www.liulongbin.top:3006/api/getbooks?id=1&bookname=%E8%A5%BF%E6%B8%B8%E8%AE%B0

1、编码与阶码
浏览器提供了URL编码与解码的API
encodeURL()编码的函数
decodeURL()解码的函数
```

### 数据交换格式

前端领域，数据交换格式是XML和JSON，重点学习JSON

#### JSON

```JavaScript
JSON就是JavaScript对象和数组的字符串表示法，它使用文本表示一个JS对象或数组的信息，JSON的本质是字符串
JSON是一种轻量级的文本数据交换格式，专门用于存储和传输数据
```

#### JSON的两种结构

```JavaScript
1、对象结构
对象结构在JSON中表示为 {} 括起来的内容，数据结构为{key:value,key:value,...} 的键值对结构，其中key必须是使用 英文的双引号包裹 的字符串，value的数据类型可以是 数字，字符串，布尔值，null，数组，对象 6种类型
对象结构为
{
    "name":"pink",
    "age":18
}
2、数组结构
数组结构在JSON种表示为 [] 括起来的内容
数组结构为["java","javascript",30,true,...]
数组中的数据类型可以是 数字，字符串，布尔值，null，数组，对象 6种类型
```

#### JSON语法注意事项

```JavaScript
1、属性名必须使用双引号包裹
2、字符串类型的值必须使用双引号包裹
3、JSON中不允许使用单引号表示字符串
4、JSON中不能写注释
5、JSON的最外层必须是对象或数组形式
6、不能使用undefined或函数作为JSON的值
//JSON的作用: 在计算机和网络之间存储和传输数据
```

JSON和JS对象的互转

```JavaScript
要实现从JSON字符串转为js对象，使用JSON.parse()方法
let obj = JSON.parse('{"name":"z","age":18}')
consol.log(obj)
转换结果	{name: 'z', age: 18}
要实现从JS对象转换为JSON字符串，使用JSON.stringify()方法
let obj = JSON.stringify({name: 'z', age: 18})
consol.log(obj)
转换结果	{"name":"z","age":18}
```

#### 序列化和反序列化

```JavaScript
把数据对象转换为字符串的过程，叫 序列化
例如: 调用JSON.stringify()函数的操作，叫做JSON序列化
把字符串转换为数据对象的过程，叫 反序列化
例如：调用JSON.parse()函数的操作，叫做JSON反序列化
```

### XHR level2新特性

1、可以设置HTTP请求的实现

2、可以使用FormData对象管理表单数据

3、可以上传文件

4、可以获得数据传输的进度信息

#### 设置HTTP请求时限

```JavaScript
timeout属性，可以设置HTTP请求时限
xhr.timeout = 3000
上面的语句，将最长的等待时间设为3000毫秒，过了这个时间，就自动停止HTTP请求，与之配套的还有一个ontimeout事件，用来指定回调函数
xhr.ontimeout = function(e){
    alert('请求超时')
}
```

#### FormData对象管理表单数据

```JavaScript
FormData对象也可以用来获取网页表单的值
示例、
<form action="" id="form1">
    <input type="text" name="uname" id="">
    <input type="password" name="password" id="">
    <button type="submit">提交</button>
</form>

//获取表单元素
let form = document.querySelector('#form1')

//监听表单的submit事件
form.addEventListener('submit',function(e){
     //阻止默认提交事件
     e.preventDefault()

     //根据form创建的FormData对象，会自动获取到表单数据并填充到FormData对象中
     let fd = new FormData(form)
     let xhr = new XMLHttpRequest()
     xhr.open('POST','http://www.liulongbin.top:3006/api/formdata')
     xhr.send(fd)
     xhr.onreadystatechange = function(){
         if(xhr.readyState === 4 && xhr.status === 200){
             //把JSON转换为JS对象
             console.log(JSON.parse(xhr.responseText))
         }
    }
})
```

#### 上传文件

```JavaScript
完整版
<div style="width: 500px;">
      <input type="file" name="" id="file" style="float: left;" />
      <button type="submit" id="button">上传文件</button>
</div>
<!-- bootstrap 进度条样式 -->
<div class="progress" style="width: 500px;">
    <div class="progress-bar progress-bar-striped active" role="progressbar" aria-valuenow="45" aria-valuemin="0" aria-valuemax="100" style="width: 0%">
       <span class="sr-only">0% Complete</span>
    </div>
</div>
<!-- 上传成功后显示的图片 -->
<img src="" alt="" id="img" />
//JS部分
//获取到上传按钮
let btn = document.querySelector("#button");
//添加点击事件
btn.addEventListener("click", function () {
    //获取到文件表单
    let file = document.querySelector("#file").files;
    if (file.length <= 0) {
        return alert("请选择上传的文件");
    }
    let fd = new FormData();
    //将用户选择的文件添加到FormData中
    fd.append("avatar", file[0]);
    let xhr = new XMLHttpRequest();
    
    //获取到bootstrap里的标签属性   
    //获取到进度条
    let progressBar = document.querySelector('.progress-bar')
    //进度文本
    let srOnly = document.querySelector('.sr-only')
	//监听上传的进度
    xhr.upload.onprogress = function(e){
       if(e.lengthComputable){
          let percentComplete = Math.ceil((e.loaded/e.total)*100)
          //把进度给到获取的元素
          progressBar.style.width = `${percentComplete}%`
          srOnly.innerHTML = `>${percentComplete}% Complete`
       }
    }
    //监听上传完成后的事件
    xhr.upload.onload = function(){
        //先移除身上所有的样式
        progressBar.className = ''
        //在添加一个完成后的样式
        progressBar.className = 'progress-bar progress-bar-success'
    }

    xhr.open("POST", "http://www.liulongbin.top:3006/api/upload/avatar");
    xhr.send(fd);
    xhr.onreadystatechange = function () {
       if (xhr.readyState === 4 && xhr.status === 200) {
         //将获取到的数据转换为JS对象
         let res = JSON.parse(xhr.responseText);
          //判断状态
         if (res.status === 200) {
            //上传成功
            document.querySelector("#img").src ="http://www.liulongbin.top:3006" + res.url;
         } else {
            //上传失败
            console.log("图片上传失败");
         }
       }
    };
});
```

#### 显示文件上传进度

```JavaScript
//创建xhr对象
let xhr = new XMLHttpRequest();
//监听上传的进度
xhr.upload.onprogress = function(e){
    //e.lengthComputable是一个布尔值，表示当前上传的资源是否具有可计算的长度
   if(e.lengthComputable){
       // e.loaded 已传输的字节
       // e.total 需要传输的总字节
       // Math.ceil() 对其进行向上取整
       let percentComplete = Math.ceil((e.loaded/e.total)*100)
       console.log(percentComplete)
   }
}
```

#### 基于bootstrap绘制进度条效果

```JavaScript
//导入bootstrap样式
<link rel="stylesheet" href="./js/bootstrap-3.4.1-dist/css/bootstrap.css">
<!-- bootstrap 进度条样式 -->		//bootstrap官网还有很多其它的进度条样式
<div class="progress" style="width: 500px;">
   <div class="progress-bar progress-bar-striped active" role="progressbar" aria-valuenow="45" aria-valuemin="0" aria-valuemax="100" style="width: 0%">
     <span class="sr-only">0% Complete</span>
   </div>
</div>

通过js控制相关属性即可实现进度条效果
let xhr = new XMLHttpRequest();

//监听上传的进度
//获取到bootstrap里的标签属性   
//获取到进度条
let progressBar = document.querySelector('.progress-bar')
//进度文本
let srOnly = document.querySelector('.sr-only')

xhr.upload.onprogress = function(e){
    if(e.lengthComputable){
       let percentComplete = Math.ceil((e.loaded/e.total)*100)
  
       //把进度给到获取的元素
       progressBar.style.width = `${percentComplete}%`
       srOnly.innerHTML = `>${percentComplete}% Complete`
    }
}
//监听上传完成后的事件
xhr.upload.onload = function(){
     //先移除身上所有的样式
     progressBar.className = ''
     //在添加一个完成后的样式
     progressBar.className = 'progress-bar progress-bar-success'
}
```

### jQuery高级用法

#### jQuery实现文件上传

```JavaScript
完整版
//HTML部分
<input type="file" name="" id="file1"/>
<button type="submit" id="btnUload">上传文件</button>
<br>
<img src="./images/loading.gif" alt="" id="loading" style="display: none;">
//JS部分
//监听到Ajax发起了
$(document).ajaxStart(function(){
     $('#loading').show()
})
//监听到Ajax结束了
$(document).ajaxStop(function(){
     $('#loading').hide()
})

$('#btnUload').on('click',function(){
     let file = $('#file1')[0].files
     if(file.length<=0){
        return alert('请选择文件在上传')
     }
     let fd = new FormData()
     fd.append('avater',file[0])
     //必须使用ajax来实现上传文件的请求  
     $.ajax({
        method:"POST",
        url:"http://www.liulongbin.top:3006/api/upload/avatar",
        data:fd,
        //不修改 contentType 属性，使用FormData默认的 contentType 值
        contentType:false,
        //不对 FormData 中的数据进行url编码，而是将 FormData 数据原样发送到服务器
        processData:false,
        success:function(res){
            console.log(res);
        }
    })
})
```

#### jQuery实现loading效果

```JavaScript
1、ajaxStart(callback)		//callback是一个回调函数
Ajax请求开始时执行
$(document).ajaxStart(function(){
     //监听Ajax开始时执行的代码
})

2、ajaxStop(callback)
Ajax请求结束时执行
$(document).ajaxStop(function(){
     //监听Ajax结束时执行的代码
})

<img src="./images/loading.gif" alt="" id="loading" style="display: none;">
//监听到Ajax发起了
$(document).ajaxStart(function(){
     $('#loading').show()	//显示loading图片
})
//监听到Ajax结束了
$(document).ajaxStop(function(){
     $('#loading').hide()	//隐藏loading图片
})

```

### axios

axios是专注于网络数据请求的库，简单易用，且轻量化

#### axios发起GET请求

```JavaScript
axios.get('url',{params:{/*参数*/}}).then(callback)

//请求的url地址
let url = 'http://www.liulongbin.top:3006/api/get'
//请求的参数
let paramsObj = {name:'zs'}
//调用axios发起get请求
axios.get(url,{parmas:paramsObj}).then(function(res){
    //此时的res不是真实的数据是axios封装好的一些参数
    //res.data才是真实的数据
    console.log(res.data);
})
```

#### axios发起POST请求

```JavaScript
axios.post('url',{/*参数*/}).then(callback)

//请求的url地址
let url = 'http://www.liulongbin.top:3006/api/post'
//上传的参数
let data = {address:'zs',location:'北京'}
//axios发起post请求
axios.post(url,data).then(function(res){
     //服务器响应的数据
     console.log(res.data)
})
```

#### 直接使用axios发起请求

```JavaScript
axios({
    method:'请求类型',
    url:'请求的地址',
    data:{/*post数据*/},
    params:{/*get参数*/},
}).then(callback)

//axios发起get请求
let btn1 = document.querySelector('#btn1')
btn1.addEventListener('click',function(){
    axios({
         method:'GET',
         url:'http://www.liulongbin.top:3006/api/get',
         parmas:{name:'zs'}
    }).then(function(res){
         console.log(res.data)
    })
})
//axios发起post请求
let btn2 = document.querySelector('#btn2')
btn2.addEventListener('click',function(){
    axios({
         method:'POST',
         url:'http://www.liulongbin.top:3006/api/post',
         data:{address:'zs',location:'北京'}
    }).then(function(res){
         console.log(res.data)
    })
})
```

# 跨域与JSONP

### 什么是同源

```JavaScript
如果两页面的协议，域名和端口都相同，则两个页面具有相同的源
```

下表给出了想对于http://www.test.com/index.html 页面的同源检测

| URL                                | 是否同源 | 原因                                      |
| ---------------------------------- | -------- | ----------------------------------------- |
| http://www.test.com/other.html     | 是       | 同源(协议、域名、端口相同)                |
| https://www.test.com/about.html    | 否       | 协议不同( http 与 https )                 |
| http://blog.test.com/movie.html    | 否       | 域名不同( www.test.com 与 blog.test.com ) |
| http://www.test.com:7001/home.html | 否       | 端口不同( 默认的 80端口与 7001端口 )      |
| http://www.test.com:80/other.html  | 是       | 同源(协议、域名、端口相同)                |

### 什么是同源策略

```JavaScript
是浏览器提供的一个安全功能，同源策略限制了从同一个源加载的文档或脚本如何与来自另一个源的资源进行交互，这是一个用于隔离潜在恶意文件的重要安全机制
//通俗理解	浏览器规定，A网站的JavaScript脚本，不允许和非同源网站C之间进行资源的交互
例、
1、无法读取非同源网站的cookie localStorage 和indexedOB
2、无法接触非同源网页的DOM
3、无法向非同源地址发送Ajax请求
```

### 跨域

```JavaScript
同源指的是两个URL的协议，域名，端口一致，反之，则是跨域
```

### 如何实现跨域数据请求

```
现如今，实现跨域数据请求，主要有JSONP和CORS
JSONP: 出现的早，兼容性好，但只支持get请求，不支持post请求
CORS: 出现的晚，它是W3C标准，属于跨域Ajax请求的根本解决方案，支持get和post，不兼容低版本的浏览器
```

### JSONP

```javascript
JSONP的实现原理，是通过script标签的src属性，请求跨域的数据接口，并通过函数调用的形式，接受跨域接口响应回来的数据
JSONP和Ajax之间没有任何联系，JSONP没有用到xhr这个对象

示例、
<script>
    function success(data){
        console.log("JSONP请求的数据是");
        console.log(data)
    }
</script>
<script src="http://www.liulongbin.top:3006/api/jsonp?callback=success"></script>
```

### jQuery中的JSONP请求

```JavaScript
jQuery提供的$.ajax()函数，除了可以发起真正的Ajax数据请求之外，还能够发起JSONP请求
 $.ajax({
    url:"http://www.liulongbin.top:3006/api/jsonp?name=za",
    // 如果使用ajax发起JSONP请求，必须指定 dataType 值为jsonp
    dataType:'jsonp',
    success:function(res){
         console.log(res);
    }
})
默认情况下，使用jQuery发起JSONP请求，会自动携带一个callback=jQueryxxx的参数，jQueryxxx是随机生成的一个回调函数的名称

自定义参数及回调函数名字
$.ajax({
     url:"http://www.liulongbin.top:3006/api/jsonp?name=za",
     // 如果使用ajax发起JSONP请求，必须指定 dataType 值为jsonp
     dataType:'jsonp',
     // 发送到服务器的参数名称   默认callback
     jsonp:'callback',		//该属性一般不会使用
     // 自定义回调函数的名称     默认会jQueryxxx 是jQuery自动生成的
     jsonpCallback:'abc',
     success:function(res){
         console.log(res);
     }
})
```

### 防抖和节流

#### 防抖

```JavaScript
防抖策略，当事件被触发时，延迟n秒后在执行回调，如果在这n秒后又被触发，则重新计时

应用场景
用户在输入框连续输入一段字符时，可以通过防抖策略，只在输入完成后，才执行查询的操作，这样可以有效减少请求次数，节约资源请求
步骤、
1、定义一个延时器id
2、定义防抖函数
3、监听到用户输入时清空延时器
```

#### 节流

```JavaScript
节流策略，减少一段时间内事件的触发频率

应用场景
1、鼠标连续不断的触发某事件(如点击事件)，只在单位时间内触发一次
2、懒加载时要监听计算滚动条的位置，但不必每次都触发，通过节流，可以降低计算的频录，而不必去浪费cpu资源
```

#### 节流阀的概念

```JavaScript
节流阀为空，表示可以执行下次操作，不为空，表示不能执行下次操作
当前操作执行完毕，必须将节流阀重置为空，表示可以执行下次操作了
每次执行操作前，必须判断
```

#### 防抖和节流的区别

```
防抖: 如果时间频繁被触发，防抖能保证只有最后一次被触发，前面 n 多次的触发会被忽略
节流: 如果时间被频繁触发，节流能够减少事件触发的频率，节流是有选择性的执行一部分事件
```

# HTTP协议加强

### 什么是HTTP协议

```
HTTP协议既超文本传输协议(Hyper Text Transfer Protocol),它规定了客户端与服务器之间进行网页内容传输时，所必须遵守的传输格式
```

### HTTP交互模型

```
HTTP协议采用了 请求/响应 的交互模型
```

### HTTP请求消息

```JavaScript
由于HTTP协议属于客户端浏览器和服务器之间的通信协议，因此，客户端发起的请求叫HTTP请求，客户端发送到服务器的消息，叫做HTTP请求消息
// 注意: HTTP请求消息又叫HTTP请求报文

请求消息组成部分
HTTP请求消息由 请求行 请求头部 空行 和 请求体 4部分组成
1、请求行
请求和由请求方式、URL和HTTP协议版本三个部分组成，之间用空格隔开
例、GET /api/getbooks?id=1 HTTP/1.1
2、请求头部
请求头部用来描述客户端的基本信息，从而把客户端相关的信息发送给服务器
例、
User-Agent 用来说明当前是什么类型的浏览器
Content-Type 用来描述发送到服务器的数据格式
Accept 用来描述客户端能够以接受什么类型的返回内容
Accept-Language 用来描述客户端期望接受那种语言的文本内容
3、空行
最后一个请求头字段的后面是一个空行，通知服务器请求头部至此结束
请求消息的空行，用来分隔请求头部与请求体
4、请求体
请求体中存放的，是要通过POST方式提交到服务器的数据
//注意: 只有POST请求才有请求体，GET请求没有请求体
```

### HTTP响应消息

```JavaScript
HTTP响应消息由状态行，响应头部，空行 和 响应体 4 个部分组成
1、状态行
状态行由HTTP协议版本、状态码 和 状态描述文本 3 个部分组成，它们之间用空格隔开
2、响应头部
响应头部用来描述服务器的基本信息，响应头部由多行 键值对组成，每行的键和值之间用英文的冒号分割
3、空行
在最后一个响应头部字段，会紧跟一个空行，用来通知客户端响应头部至此结束
响应消息的空行，用来分割响应头部和响应体
4、响应体
响应体中存放的是服务器响应给客户端的资源内容
```

### HTTP请求方法

```JavaScript
请求方法，属于HTTP协议中的一部分，请求方法的作用是: 用来表明 要对服务器上的资源执行的操作，最常用的请求方式是 GET 和 POST
GET (查询)发送请求来获得服务器上的资源
POST (新增)向服务器提交资源
PUT (修改)向服务器提交资源，并使用提交的新资源，替换到服务器对应的旧资源
DELETE (删除)请求服务器删除指定的资源
```

### HTTP响应状态码

```JavaScript
HTTP响应状态码(HTTP Status Code)也属于HTTP协议的一部分，用来标识响应的状态
响应状态码会随着响应消息一起被发送至客户端浏览器，浏览器根据服务器返回的响应状态码，就知道这次HTTP请求的结果是成功还是失败了
```

响应状态码的组成及分类

| 分类 | 分类描述                                       |
| ---- | ---------------------------------------------- |
| 1**  | 信息，服务器收到请求(了解即可，很少遇到)       |
| 2**  | 成功，操作被成功接收并处理                     |
| 3**  | 重定向，需要进一步的操作完成以下请求           |
| 4**  | 客户端错误，请求包含语法错误或无法完成请求     |
| 5**  | 服务器错误，服务器在处理请求的过程中发生了错误 |

2**成功相关的状态码

2**范围的状态码，标识服务器已成功接收到请求并进行处理

| 装态码 | 状态码和英文名称 | 中文描述                                                |
| ------ | ---------------- | ------------------------------------------------------- |
| 200    | OK               | 请求成功，一般用于GET或POST请求                         |
| 201    | Created          | 已创建，成功请求并创建了新的资源，通常用于POST或PUT请求 |

3**重定向相关的状态码

3**范围的状态码，表示服务器要求客户端重新定向，需要客户端进一步操作以完成资源的请求

| 状态码 | 状态码英文名称    | 中文描述                                                     |
| ------ | ----------------- | ------------------------------------------------------------ |
| 301    | Moved Permanently | 永久移动，请求的资源已被永久移动到新的URL，返回信息会包括新的URL，浏览器会自动定向到新的URL，今后任何新的请求都应使用新的URL代替 |
| 302    | Found             | 临时移动，与301类似，但资源只是被临时移动，客户端继续使用原有的URL |
| 304    | Not Modified      | 未修改，所请求的资源未被修改，服务器返回此状态码，不会返回任何资源(响应消息不包含响应体)客户端通常会缓存访问过的资源 |

4**客户端错误相关的状态码

4**范围的状态码，表示客户端的请求有非法内容，从而导致这次请求失败

| 状态码 | 状态码英文名称  | 中文描述                                       |
| ------ | --------------- | ---------------------------------------------- |
| 400    | Bad Request     | 1、语义有误，2、请求参数有误                   |
| 401    | Unanthorized    | 当前请求需要用户验证                           |
| 403    | Forbidden       | 服务器已经理解请求，但是拒绝执行它             |
| 404    | Not Found       | 服务器无法根据客户端的请求找到资源(网页)  重点 |
| 408    | Request Timeout | 请求超时                                       |

5**服务器端错误状态码

5**范围的状态码，表示服务器未能正常处理客户端的请求而出现的意外错误

| 状态码 | 状态码英文名称       | 中文描述                                                     |
| ------ | -------------------- | ------------------------------------------------------------ |
| 500    | Internal Sever Error | 服务器内部错误，无法完成请求                                 |
| 501    | Not Implemented      | 服务器不支持该请求方法，无法完成请求，只有GET和HEAD请求方法是要求每个服务器必须支持的，其它请求方法在不支持的服务器上会返回501 |
| 503    | Service Unavailable  | 由于超载或系统维护，服务器暂时无法处理客户端的请求           |

