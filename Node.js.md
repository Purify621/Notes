# Node.js

Node.js 是一个基于 chrome v8 引擎的 JavaScript 环境

### Node.js 中的 JavaScript 运行环境

注意：

1、浏览器是 JavaScript 的前端运行环境

2、Node.js 是 JavaScript 的后端运行环境

3、Node.js 中无法调用 DOM 和 BOM 等浏览器内置 API

### Node.js 可以做什么

Node.js 作为一个 JavaScript 的运行环境，仅仅只提供了基础的功能和API 但是当学会 Node.js 可以让我们去更好的学习更强大的工具和框架

1、基于EXpress框架	可以快速搭建web应用

2、基于Electron框架	可以构建跨平台的桌面应用

3、基于restify	可以快速构建API接口项目

4、读写和操作数据库

### 查看已安装的Node,js版本号

在终端，输入命令 node -v 即可查看版本号

### 在 Node.js环境中执行JavaScript代码

1、打开代码

2、输入 **node** 要执行的 js 文件的路径

### 终端中的快捷键(部分)

1、使用 方向键的 ↑ 键 可以快速定位到上一次执行的命令

2、使用 tab 键 能够快速补全路径

3、使用 esc 键能够快速清空当前已输入的命令

4、cls 清空当前终端

# fs文件系统模块

fs模块是Node.js官方提高的，用来操作文件的模块，它提供了一系列方法和属性，用来满足用户对文件的操作需求

fs.readFIle() 方法，用来读取指定文件的内容

fs.writeFile() 方法，用来向指定的文件中写入内容

如果要在JavaScript代码中，使用fs模块来操作文件，则需要使用如下的方式导入它

const fs = require('fs')

### fs.readFile( )  读取指定文件的内容

```javascript
使用fs.readFile()方法，可以读取指定文件的内容 语法格式如下
fs.readFile(path[,options],callback)
参数
1、path	必选参数，字符串，表示文件的路径
2、options	可选参数，表示以什么编码格式来读取文件
3、callback	必选参数，文件读取完成后，通过回调函数拿到读取的结果

示例代码
 //1、导入 fs 模块
const fs = require('fs')

//调用 readFile()方法读取文件
//  参数1 文件存放的路径
//  参数2 读取文件时采用的编码格式  一般默认指定utf8
//  参数3 回调函数，拿到读取成功和失败的结果    err dataStr
fs.readFile('./file/1.txt','utf8',function(err,dataStr){
    //  2.1打印失败的结果
    //  如果读取成功 err的默认值为null  
    //如果读取失败，则err的值为错误对象 dataStr的值为undefined
    console.log(err);
    console.log('~~~~~~~')
    //  2.2打印成功的结果
    console.log(dataStr)
})

//注意: null不是数值，该方法先尝试转为数值再判断，null转为数值是0，所以结果是false.
判断文件是否读取成功
fs.readFile('./file/1.txt','utf8',function(err,dataStr){
    //如果读取成功则err的值为 null ，null在判断中会被解析为false 因此不会执行判断里面的代码，就可以知道是读取成功了，如果不为null则是读取失败
	if(err){
        return console.log('文件读取失败',+err.message)
    }
    console.log('文件读取成功，内容是'+ dataStr)
})
```

### fs.writeFile( ) 向指定文件中写入内容

```javascript
使用 fs.writeFile()方法，可以向指定的文件中写入内容
fs.writeFile(file,data[,options],callback)

参数
1、file	必选参数，需要指定一个文件的路径的字符串，表示文件存放的路径
2、data	必选参数，表示要写入的内容
3、options	可选参数，表示以什么格式写入文件内容，默认值是utf8
4、callback	必选参数，文件写入完成后的回调函数

示例、
//1、导入fs文件系统模块
const fs =  require('fs')
//调用 fs.writeFile() 方法，写入文件的内容
fs.writeFile('./file/2.txt','abcd',function(err){
    //如果文件写入成功则err为null
    //如果文件写入失败，则err的值为一个错误对象
    //判断 err 的值，为null则文件写入成功，否则失败
    if(err){
        return console.log('文件写入失败'+err.message)
    }
    console.log('文件写入成功')
})

/*
注意
1、fs.writeFile() 方法只能用来创建文件，不能用来创建路径
2、重复调用 fs.writeFile() 写入同一个文件，新写入的文件会覆盖之前的旧内容
*/
```

## fs模块-路径动态拼接的问题

在使用fs模块操作文件时，如果提供的操作路径是以 ./ 或 ../ 开头的相对路径时，很容易出现路径动态拼接错误的问题

原因：代码在运行的时候，会让执行 node 命令时所处的目录，动态拼接出被操作文件的完整路径

**解决方案**

使用 __dirname	表示当前文件所处的目录，在拼接上需要读取的目录即可找到该文件

```JavaScript
//读取文件示例
fs.readFile(__dirname+'/file/1.txt','utf8',function(err,dataStr){
    if(err){
        return console.log('读取文件失败',err.message);
    }
    console.log('获取数据成功',dataStr)
})
```

# path路径模块

path模块是Node.js官方提供的，用来处理路径的模块，它提供一系列的方法和属性，用来满足用户对路径处理需求

path.join( ) 方法，用来将多个路径片段拼接成一个完整的路径字符串

path.basename( )方法，用来从路径字符串中，将文件名解析出来

如果要在 JavaScript 代码中，使用 path 模块来处理路径，则需要使用如下的方式先导入它

const path = require('path')

### path.join( )  路径拼接

```JavaScript
使用path.join()方法，可以把多个路径片段拼接为完整的字符串
语法
path.join([...paths])
参数
...paths <string> 路径片段的序列
返回值 <string>

示例、
//注意 ../ 会抵消一层路径
读取文件
const fs = require('fs')
const path = require('path')

fs.readFile(path.join(__dirname,'/file/1.txt'),'utf8',function(err,dataStr){
    if(err){
        console.log(err.message)
    }
    console.log(dataStr)
})
今后凡是涉及到路径拼接的操作，都要使用path,join()方法进行处理
```

### path.basename( ) 获取路径中的文件名

```JavaScript
使用 path.basename()方法，可以获取路径中的最后一部分，经常用这个方法获取路径中的文件名
path.basename(path[,ext])
参数
path 必选参数，表示一个路径的字符串
ext 可选参数，表示文件扩展名
返回	表示路径中的最后一部分

示例、
const path = require('path')
const fpath = '/a/b/c/index.html'

const fullpath = path.basename(fpath)
//不传递参数会获取到  index.html
console.log(fullpath);

const fullpath1 = path.basename(fpath,'.html')
//传递参数会把 .html给过滤掉，得到 index
console.log(fullpath1)
```

### path.extname( ) 获取路径中的文件扩展名

```javascript
使用path.extname()方法，可以获取路径中的扩展名部分
path.extname(path)
参数
path	必选参数，表示一个路径的字符串
示例、
const path = require('path')
const fpath = '/a/b/c/index.html'
const fext = path.extname(fpath)
//会获取到路径文件的扩展名  .html
console.log(fext);
```

# HTTP模块

http模块是 Node.js 官方提供的，用来创建 web 服务器的模块，通过 http 模块 提供的 http.createServer( ) 方法，就能方便的把一台电脑，变成一台web服务器，从而对外提供web资源服务

如果希望使用 http 模块创建 web 服务器 ，则需要先导入它

const http = require('http')

## 创建最基本的web服务器

### 步骤

```javascript
1、导入http模块
const http = require('http')

2、创建web服务器实例
const server = http.createServer()

3、为服务器实例绑定 request 事件，监听客户端请求
server.on('request',function(req,res){
	//只要有客户端请求我们自己的服务器，就会触发 request 事件，从而调用这个事件处理函数
	console.log()
})

4、启动服务器
调用服务器实例的 .listen()方法，即可启动当前的 web 服务器实例
// 调用 server.listen(端口号,callback回调)方法，即可启动 web 服务器
server.listen(80,()=>{
	console.log('http server ruuuing at http:127.0.0.1')
})
```

### req 请求对象

只要服务器接受了客户端的请求，就会调用通过 server.on( ) 为服务器绑定的 request 事件处理函数

如果想在事件处理函数中，访问与客户端相关的数据或属性，可以使用如下的方式

```JavaScript
实例、
const http = require('http')
const server = http.createServer()
    //req 是请求对象，包含了与客户端相关的数据和属性
server.on('request',(req)=>{
    // req.url 是客户端请求的url地址
    const url = req.url
    // req.method 是客户端请求的method类型
    const method = req.method
    const str = `your request url is ${url},and request method is ${method}`
    console.log(str)
})
server.listen(80,()=>{
    console.log('server at http://127.0.0.1')
})
```

### res响应对象

res.end( ) 方法，可以向客户端发送指定的内容，并结束这次请求的处理

```JavaScript
实例、
const http = require('http')
const server = http.createServer()
    //req 是请求对象，包含了与客户端相关的数据和属性
server.on('request',(req,res)=>{
    // req.url 是客户端请求的url地址
    const url = req.url
    // req.method 是客户端请求的method类型
    const method = req.method

    const str = `your request url is ${url},and request method is ${method}`

    //通过 res.end() 向客户端响应一些内容
    res.end(str)
})
server.listen(80,()=>{
    console.log('server at http://127.0.0.1')
})
```

解决中文乱码的问题

当调用res.end( ) 方法，向客户端发送中文的内容时，会出现乱码问题，此时，需要手动设置内容的编码格式 

res.setHeader('Content-Type',' text / html ; charset = utf-8 ')	固定写法

```JavaScript
代码示例、
const http = require('http')

const server = http.createServer()
server.on('request',(req,res)=>{
    //定义一个字符串 内容包含中文
    const str = `你的url地址是${req.url}:请求类型是${req.method}`
    //解决中文乱码
    res.setHeader('Content-Type','text/html; charset=utf-8')
    res.end(str)
})

server.listen(80,()=>{
    console.log('server runing http://127.0.0.1')
})
```

### 根据不同的url来响应不同的内容

```JavaScript
1、获取请求的url地址
2、设置响应的默认值为404 Not found
3、判断用户输入请求是否为 / 或 /index.html
4、判断用户输入请求是否为 /about.html 关于页面
5、设置Content-Type 响应头，防止中文乱码
6、使用res.end() 把内容响应给客户端
示例、
const http = require("http");
const server = http.createServer();
server.on("request", (req, res) => {
	//1、获取url地址
    const url = req.url;
    //2、设置默认的访问为   文本变量要用 let 来接受
    let Content = "<h1>404 is Not undefined</h1>"
    //3、判断用户输入的是否是主页或者index.html页面
    if(url === "/" || url === "/index.html"){
        Content = "<h1>访问的是首页</h1>"
    }else if(url === '/about.html'){       //4、判断用户输入是否是关于页面
        Content = "<h1>关于页面</h1>"
    }
    //5、解决中文乱码问题
    res.setHeader('Content-Type','text/html; charset=utf-8')
    //6、响应给客户端
    res.end(Content)
});
server.listen(80, () => {
  console.log("server runing http://127.0.0.1");
});
```

# 模块化

编程领域的模块化，就是遵守固定的规则，把一个大文件拆成独立并相互依赖的多个小模块

代码拆分的好处

1、提高了代码的复用性

2、提高了代码的可维护性

3、可以实现按需加载

### Node的三大模块

内置模块，用户自定义模块，第三方模块

### 加载模块

require( ) 方法，可以加载需要的内置模块，用户自定义模块，第三方模块进行使用

```javascript
1、加载内置模块
const fs = require('fs')
2、加载用户自定义模块
const custom = require('./custom.js')
3、加载第三方模块
const moment = require('moment')
当使用require()方法加载其它模块时，会执行被加载模块中的代码
//在使用require加载用户自定义模块期间，可以省略.js的后缀名
```

### 模块作用域

在自定义模块中定义的变量，方法等成员，只能在当前的模块内被访问，这种模块级别的访问限制，叫做模块作用域

### 向外共享模块作用域中的成员

**1、module 对象**  代表当前这个对象，里面包含了当前对象的信息

2、**module.exports( )**	对象，在自定义模块，可以使用 module.exorts 对象，将模块内的成员共享出去，供外界使用，外界用 require()方法导入自定义模块时，得到的就是 module.exports 所指向的对象

```JavaScript
示例、
//向 module.exports 对象上挂载 username 属性
module.exports.username = ''
//向 module.exports 对象上挂在 sayHallo 方法
module.exports.sayHallo = function(){
	console.log('hallo!')
}

此时在访问该自定义模块时，就能拿到这两个属性了
```

**3、共享成员时的注意点**

使用require() 方法导入模块时，导入的结果，永远以 module.exports 指向的对象为准

**4、exports对象**

由于module.exports 写起来比较复杂，为了简化向外共享成员的代码，Node提供了 exports 对象 默认情况下，exports 和 module.exports 指向同一个对象，最终共享的结果，还是以 module.exports指向的对象为准

exports 和 module.exports 的使用误区

时刻谨记，require() 模块时，得到的永远是 module.exports 指向的对象

注意: 为了防止混乱，建议不要在同一个模块中同时使用 exports 和module.exports

### Node.js模块化规范

Node.js 遵循了 CommonJS 模块化规范，CommonJS 规定了模块的特性和和模块之间如何相互依赖

```JavaScript
CommonJS规定
1、每个模块内部，module 变量代表当前模块
2、module 变量是一个对象，它的 exports 属性 (既 module.exports)是对外的接口
3、加载某个模块，其实是加载该模块的 module.exports 属性 ，require() 方法用于加载模块
```

# npm与包

## 什么是包

Node.js中的第三方模块又叫做包

### 包的来源

不同于Node.js中的内置模块与自定义模块，包是由第三方个人或团队开发出来的，免费供所有人使用 	Node.js中的包都是免费开源的

### 为什么需要包

包是基于内置模块封装出来的，提供了更高级，更方便的API，能极大的提高开发效率

### 在项目中安装包的命令

```JavaScript
如果想在项目中安装指定名称的包，需要运行如下的命令
npm install 包的完整名称
简写形式
npm i 完整的包名称
```

### 初次装包的文件

node_modules 文件夹用来存放所有已安装到项目中的包，require( ) 导入第三方包时，就是从这个目录中查找并加载包

package-look.json 配置文件用来记录 node_modules 目录下的每一个包的下载信息

### 安装指导版本的包

```javascript
在报名之后通过 @符号指导版本
npm i moment@2.22.2
```

### 快速创建package.json

```JavaScript
npm包管理工具提供了一个快捷命令，可以在执行命令时所处的目录中，快速创建packag.json这个包管理文件
npm init -y
//注意
1、上述命令只能在英文的目录下正常运行，所以，项目文件夹的名称一定要使用英文名称，不要使用中文，不能出现空格
2、运行 npm install 命令安装包时，npm包管理工具会自动把包的名称和版本号 记录到 package.json中
```

### dependencies 节点

专门用来记录使用 npm instal 命令安装了哪些包 

### 一次性安装所以的包

```javascript
当我们拿到了一个剔除了 node_modules 的项目之后，需要先把所有的包下载到项目中，才能将项目运转起来
可以运行 npm install 命令或者 npm i 一次性安装所有的依赖包
```

### 卸载包

npm uninstall 包的名字	来卸载指定的包

例、npm uninstall moment 	命令运行成功后，会把卸载的包，自动从package.json 的 dependencies 中移除掉

### devDependencies	节点

```JavaScript
如果某些阶段只在项目开发阶段会用到，在项目上线之后不会用到，则把这些节点记录到 devDependencies 节点中
安装指定的包，并记录到 devDependencies 节点中
npm i 包名 -D
// 注意 上述命令是简写形式，等价于下面的完整写法
npm install 包名 --save-dev
```

### 解决下包慢的问题

```JavaScript
查看当下的下包镜像源
npm config get registry
将下包的镜像源切换为淘宝镜像源
npm config set registry=http://registry.npm.taobao.org/
检查镜像源是否更改成功
npm config get registry
```

### nrm工具切换下包服务器

```javascript
为了更方便的切换下包的镜像源，我们可以安装nrm这个小工具，利用nrm提供的终端命令，可以快速查看和切换下包的镜像源
//	通过 npm 包管理工具，将 nrm 安装为全局可用的工具
npm i nrm -g
//	查看所有可用的镜像源
nrm ls
//	将下包的镜像源切换为 taobao 镜像
nrm use taobao
```

## 包的分类

使用npm包管理工具下载的包，共分为两大类，分别是 项目包和全局包

```JavaScript
项目包	//那些被安装到项目的 node_modules 目录中的包，都是项目包
项目包又分为
开发依赖包	//( 被记录到 devDependencies 节点中的包，只在开发期间会用到 )
核心依赖包	//( 被记录到 denpendencies 节点中的包，在开发期间和项目上的线之后都会用到 )
npm i 包名 -D		开发依赖包
npm i 包名		核心依赖包

全局包
在执行 npm install 命令时，如果提供了 -g 参数，则会把包安装为全局包
默认安装位置	C:\Users\ME\AppData\Roaming\npm\node_modules
npm i 包名 -g 	全局安装指定的包
npm uninstall 包名 -g		卸载全局安装的包
/*
注意
1、只有工具性质的包，才有全局安装的必要性，因为它们提供了好用的终端命令
2、是否全局安装，看官方文档说明即可
*/
```

### i5ting_toc  md转html页面小工具

i5ting_toc 是一个可用把 md文档转为html页面的小工具 

```JavaScript
//将 i5ting_toc 安装为全局包
npm install -g i5ting_toc
//调用 i5ting_toc 轻松实现 md 转 html 的功能
i5ting_toc -f 要转换的md文件路径 -o
```

### 规范的包结构

```JavaScript
一个规范的包结构，必须符合以下3点要求
1、包必须以单独的目录存在
2、包的顶级目录下要求必须包含 package.json 这个包管理配置文件
3、package.json 中必须包含 name，version，main这三个属性，分别代表包的名字，版本号，包的入口
```

## 开发属于自己的包

初始化包的基本结构

```JavaScript
1、新建一个文件夹，作为包的根目录
2、在新建文件夹中，新建如下三个目录
	package.json	包管理配置文件
	index.js		包的入口文件
	README.md		包的说明文档
```

### 登录 npm 账号

```JavaScript
npm 账号注册完成后，可以在终端中执行 npm login 命令，依次输入用户名，密码，邮箱后，即可登录成功
//注意 在运行 npm login 命令之前，必须先把下包的服务器地址切换为 npm 的官方服务器 否则会导致发布包失败
```

### 发布包到npm上

```JavaScript
将终端切换到包的根目录之后，运行 npm publish 命令，即可将包发布到npm上 (注意: 包名不能雷同)
```

### 如何删除已发布的包

```JavaScript
运行 npm unpublish 包名 --force 命令，即可从npm删除已发布的包
注意
1、npm unpublish 命令只能删除72小时以内的包
2、npm unpublish 删除的包，在24小时内不允许重复发布
3、发布包时要慎重，尽量不要往npm上发布没有意义的包
```

## 模块的加载机制

### 优先从缓存中加载

```JavaScript
模块在第一次加载后会被缓存，这也意味着多次调用 require( ) 不会导致模块的代码被执行多次

注意: 不论是内置模块、用户自定义模块、还是第三方模块，它们都会优先从缓存中加载，从而提高模块的加载效率
```

### 内置模块的加载机制

```JavaScript
内置模块是由 Node.js 官方提供的模块，内置模块的加载优先级最高

例如、require( 'fs' ) 始终返回内置的 fs 模块，即使在 node_modules 目录下有名字相同的包也叫做 fs
```



### 自定义模块的加载机制

```JavaScript
使用 require ( ) 加载自定义模块时，必须指定 ./ 或 ../ 开头的路径标识符，在加载自定义模块时，如果没有指定 ./ 或 ../ 这样的路径标识符，则node 会把它当作内置模块或第三方模块进行加载

同时，在使用 require ( ) 导入自定义模块时，如果省略了文件的扩展名，则 Node.js 会按顺序分别尝试加载以下文件
1、按照确切的文件名进行加载
2、补全 .js扩展名进行加载
3、补全 .json 扩展名进行加载
4、补全 .node 扩展名进行加载
5、报错，加载失败
```

### 第三方模块加载机制

```JavaScript
如果传递给 require() 的模块标识符不是一个内置模块，也没有以 ./ 或 ../ 开头，则Node.js会从当前的模块的父目录开始，尝试从 /node_modules 文件夹中加载第三方模块

如果没有找到对应的第三方模块，则移动到再上一层的父目录中，进行加载，直到系统的根目录
```

### 目录作为模块

```JavaScript
当把目录作为模块标识符，传递给require()进行加载的时候，有三种加载方式
1、在被加载的目录下查找一个叫做 package.json 的文件，并寻找main属性，作为 require()加载的入口
2、如果目录中没有package.json文件，或者main入口不存在或无法解析，则Node.js会试图加载目录下的index.js文件
3、如果上两步加载都失败了。则Node.js 会在终端打印错误消息，报告模块的缺失
```

# Express

```JavaScript
1、Express 是基于 Node.js 平台，快读、开放、极简的 web 开发框架
2、Express 的作用和 Node.js 内置的 http 模块类型，是专门用来创建 web服务器的
3、Express 本质就是 一个npm上的第三方包，提供了快速创建 web 服务器的便捷方法
4、使用 Express 我们可以方便、快速的创建 web 网站的服务器或 API 接口的服务器
```

### 安装

```javascript
npm i express@4.17.1	//安装的是指定版本

官网
https://www.expressjs.com.cn/
也可以在官网直接找到安装的命令 
```

### 创建基本的 web 服务器

```JavaScript
// 1、导入express
const express = require('express')
// 2、创建web服务器
const app = express()
// 3、启动web服务器
app.listen(80,()=>{
    console.log('express server runing at http://127.0.0.1')
})
```

### 监听客户端 GET 或 POST 请求 以及响应客户端

```JavaScript
1、通过 app.get()方法，可以监听客户端的 GET 请求
app.get('请求URL',(req,res)=>{/*处理函数*/})
2、通过 app.post()方法，可以监听客户端的 POST 请求
app.post('请求URL',(req,res)=>{/*处理函数*/})

参数1、客户端请求的 URL 地址
参数2、请求对应的处理函数
req: 请求对象(包含了与请求相关的属性与方法)
res: 响应对象(包含了与响应相关的属性与方法)

3、把内容响应给客户端
通过res.send()方法，可以把处理好的内容，发送给客户端

示例、
//监听客户的 GET 或 POST 请求，并向客户端响应具体的内容
app.get('/user',(req,res)=>{
    //调用 express 提供的 res.send() 方法，向客户端响应一个 JSON对象
    res.send({name:'zs',age:20})
})
app.post('/user',(req,res)=>{
    //调用 express 提供的 res.send() 方法，向客户端响应一个 文本字符串
    res.send('请求成功')
})
```

### 获取URL中所携带的查询参数

```JavaScript
通过 req.query 对象，可以访问到客户端通过查询字符串的形式，发送到服务器的参数
app.get('/',(req,res)=>{
    // 通过 req.query 可以获取到客户端发送过来的查询参数
    //注意: 默认情况下 req.query 是一个空对象
    console.log(req.query)
    res.send(req.query)
})
示例
/*
客户端使用 ?name=zs&age=20
此时通过 req.query 对象能访问到传递的数值
{
   "name": "za",
   "age": "20"
}
req.query.name 或 req.query.age 能拿到具体的值
*/
```

### 获取URL中的动态参数

```JavaScript
通过 req.params 对象，可以访问到URL中，通过 : 匹配到的动态参数
// 注意 这里的 id 是一个动态的参数
app.get('/user/:id',(req,res)=>{
    // req.params 是动态匹配到的 URL 参数 默认是一个空对象
    res.send(req.params)
})

//注意点
1、: 后面的名称可以随意写，只要符合规定
2、/user/:id/:name 可以同时匹配多个动态参数

url里传递参数的形式
http://127.0.0.1/user/1
http://127.0.0.1/user/1/zs
```

### 托管静态资源

```JavaScript
1、express.static()
通过该函数，我们可以非常方便的创建一个静态资源服务器
例如、通过如下代码就可以将public 目录下的图片、css文件、JavaScript对外开放访问了
app.use(express.static('public'))
注意、Express 在指定的静态目录中查找文件，并对外提供资源的访问路径，因此，存放静态文件的目录不会出现在URL中
```

### 托管多个静态资源目录

```JavaScript
如果要托管多个静态资源目录，请多次调用express.static()函数
例、
app.use(express.static('public'))
app.use(express.static('files'))
托管了两个文件夹
访问静态资源文件时，express.static()函数会根据目录的添加顺序查找所需的文件
```

挂载路径前缀

```JavaScript
如果希望在托管的静态资源访问资源之前，挂载路径前缀，则可以使用如下的方式
app.use('./public',express.static('public'))
现在，就可以通过带有/public 前缀地址来访问 public 目录中的文件了
http://127.0.0.1/clock/index.html
```

## nodemon工具

```JavaScript
nodemon 在我们修改代码时，会自动的帮我们重启服务器，不需要再手动重启，极大的方便了开发和调试
```

### 安装

```JavaScript
npm install -g nodemon
npm i -g nodemon
```

### 使用

```JavaScript
将之前的 node 命令改为 nodemon 来启动项目，这样代码被修改后，会被 nodemon 监听到，从而实现自动重启的效果
例、
nodemon app.js 
```

## express路由

```JavaScript
在 express 中，路由指的是客户端的请求与服务器处理函数之间的映射关系
express 的路由分3部分组成，分别是 请求的类型、请求的url地址、处理函数，格式如下
app.METHOD(PATH,HANDLER)
METHOD 值可以是 GET 或 POSY
PATH 请求的地址
HANDLER	处理函数

路由例子、
匹配GET请求
app.get('/',(req,res)=>{
    res.send('Hello,world!')
})
匹配POST请求
app.post('/',(req,res)=>{
    res.send('Got a POST request')
})
```

### 路由最简单的用法

```JavaScript
在 express 中使用路由最简单的方式，就是把路由挂载到服务器上
示例、
const express = require('express')
//创建web服务器
const app = express()

//挂载路由
app.get('/',(req,res)=>{
    res.send('Hello world')
})

app.post('/',(req,res)=>{
    res.send('post request')
})
//启动web服务器
app.listen(80,()=>{
    console.log('express server runing http://127.0.0.1');
})
```

### 模块化路由

```JavaScript
为了方便对路由进行模块化的管理，express 不建议将路由直接挂载到app上，而是推荐将路由抽离为单独的模块
抽离路由的步骤
1、创建路由模块对应的 .js 文件
2、调用 express.Router() 函数创建路由对象
3、向路由对象上挂载具体的路由
4、使用 module.expors 向外共享路由对象
5、使用 app.use() 函数注册路由模块

示例、
//这是路由模块
const express = require('express')
//2、创建路由对象
const router = express.Router()
//3、挂载路由
router.get('/uese/list',(req,res)=>{
    res.send('Get user list')
})
router.post('/user/add',(req,res)=>{
    res.send('Post user add')
})
//4、向外导出路由对象
module.exports = router

// 使用模块化路由
const express = require('express')
const app = express()
//1、导入路由模块
const router = require('./05.router')
//2、挂载路由
app.use(router)		//app.use() 函数的作用，就是来注册全局中间件
app.listen(80,()=>{
    console.log('http://127.0.0.1');
})
```

### 为路由模块添加前缀

```JavaScript
//1、导入路由模块
const router = require('./05.router')
//2、挂载路由
app.use('/api',router)	
```

## express中间件

```JavaScript
1、中间件的调用流程
当一个请求到达 express 的服务器之后，可以连续调用多个中间件，从而对这次请求进行预处理

2、中间件的格式
express 的中间件，本质上就是一个 function 处理函数
注意: 中间件函数的形参列表中，必须包含 next 函数，而路由处理函数中只包含 req 和 res
```

### next 函数的作用

```JavaScript
next 函数是实现多个中间件连续调用的关键，它表示把流转关系转交给下一个中间件或路由
```

### 定义中间件函数

```JavaScript
最简单的中间件函数
const express = require('express')
const app = express()
//定义一个中间件函数
const mw = function(req,res,next){
    console.log('这是最简单的中间件函数')
    // 把流转关系转交给下一个中间件或路由
    next()
}
app.listen(80,()=>{
    console.log('http://127.0.0.1');
})
```

### 全局生效的中间件

```JavaScript
客户端发起的任何请求，到达服务器之后，都会触发的中间件，叫做全局中间件
通过调用 app.use(中间件函数) 即可定义一个全局生效的中间件

示例、
//定义一个中间件函数
const mw = function(req,res,next){
    console.log('这是最简单的中间件函数')
    // 把流转关系转交给下一个中间件或路由
    next()
}
// 将 mw 注册为全局生效的中间件
app.use(mw)
```

### 定义全局中间件的简化形式

```JavaScript
app.use(function(req,res,next){
    console.log('这是一个简单的中间件函数')
    next()
})
```

### 中间件的作用

```JavaScript
多个中间件之间，共享同一份 req 和 res 基于这样的特性，我们可以在上游的中间件中，统一为 req 和 res 对象添加自定义属性和方法，供下游的中间件或路由进行使用
// 示例
app.use(function(req,res,next){
    const time = Date.now()
    // 为 req 对象，挂载自定义属性，从而把时间共享给后面所有的路由
    req.startTime = time
    next()
})
app.get('./',(req,res)=>{
    res.send('home page'+req.startTime)		//下游也可以访问到上游定义的 req.startTime 属性
})
app.get('/user',(req,res)=>{
    res.send('user page'+req.startTime)
})
```

### 定义多个全局中间件

```JavaScript
可以使用 app.use() 连续定义多个全局中间件，客户端请求到达服务器之后，会按照中间件定义的先后顺序依次进行调用
// 示例
const express = require('express')
const app = express()
//定义第一个中间件函数
app.use((req,res,next)=>{
    console.log('第一个中间件函数')
    next()
})
//定义第二个中间件函数
app.use((req,res,next)=>{
    console.log('第二个中间件函数')
    next()
})
//定义路由
app.get('/user',(req,res)=>{
    res.send('user page')
})
app.listen(80,()=>{
    console.log('http://127.0.0.1');
})
// 会依次调用中间间函数
```

### 局部生效的中间件

```JavaScript
不使用 app.use() 定义的中间件，叫做局部生效的中间件
// 示例
//定义中间件
const mw1 = (req,res,next)=>{
    console.log('局部生效的中间件函数')
    next()
}
// 创建路由
//mw1 中间件函数只在当前路由生效，这种用法属于 局部中间件函数 
app.get('/',mw1,(req,res)=>{    
    res.send('home page')
})
```

### 定义多个局部的中间件

```JavaScript
可以在路由中，通过如下两个等价的方式，使用任意多个局部中间件
app.get('/',mw1，mw2,(req,res)=>{    
    res.send('home page')
})
app.get('/',[mw1，mw2],(req,res)=>{    
    res.send('home page')
})
```

### 中间件的5个使用注意事项

```JavaScript
1、一定要在路由之前注册中间件
2、客户端发送过来的请求，可以连续调用多个中间件进行处理
3、执行完中间件的业务代码之后，不要忘记调用 next() 函数
4、为了防止代码逻辑混乱，调用完 next() 函数后不要在写额外的代码
5、连续调用多个中间件时，多个中间件之间，共享 req 和 res 对象
```

## 中间件的分类

### 1、应用级别的中间件

```JavaScript
通过 app.use() app.get() app.post() 绑定到 app 实例上的中间件，是应用级别的中间件
// 示例
app.use((req,res,next)=>{
    next()
})
app.get('/',mw1,(req,res)=>{
    next()
})
```

### 2、路由级别的中间件

```JavaScript
绑定到 express.Router() 实例上的中间件，叫做路由级别的中间件、示例代码
const app = express()
const router = express.Router()
router.use((req,res,next)=>{
    next()
})
```

### 3、错误级别的中间件

```JavaScript
错误级别中间件的作用，专门用来捕获整个项目中发生的异常错误，从而防止项目异常崩溃的问题
格式: 错误级别中间件的 function ;处理函数中，必须有4个参数,(err,req,res,next)
// 注意 错误级别的中间件，必须注册在所有路由之后
// 示例
app.get('/',(req,res)=>{
    // 定义一个人为的错误
    throw new Error('服务器内部放生错误')
    res.send('home page')
})
// 错误级别的中间件
app.use((err,req,res,next)=>{
    // 在服务器打印错误消息
    console.log('发生了错误'+err.message)
    //向客户端响应错误消息
    res.send('error'+err.message)
})
```

### 4、express内置的中间件

```JavaScript
4.1、express.static 快速托管静态资源的内置中间件，例如、HTML文件、图片、css样式等(无兼容性)
4.2、express.json 解析 JSON 格式的请求体数据(有兼容性，仅在4.16.0+版本中使用)
//配置解析、application/json 格式数据的内置中间件
app.use(express.json())
4.3、express.urlencoded 解析 URL-encoded 格式的请求体数据(有兼容性、仅在4.16.0+版本中使用)
//配置解析，application/x-www-form-urlencoded 格式数据的内置中间件
app.use(express.urlencoded({extended:false}))
```

#### express.json( )

```javascript
演示
const express = require('express')
const app = express()
//通过 express.json()这个中间件，解析表单中的JSON格式的数据
app.use(express.json())

app.post('/user',(req,res)=>{
    //在服务器，可以通过 req.body 这个属性，来接受客户端发送过来的请求体数据
    //默认情况下，如果不配置解析表单的中间件，则 req.body 默认等于undefined
    console.log(res.body)
    res.send('ok')
})
app.listen(80,()=>{
    console.log('http://127.0.0.1');
})
```

#### express.urlencoded( )

```javascript
//通过 express.urlencoded() 这个中间件，来解析 表单中的 url-encoded 格式的数据
app.use(express.urlencoded({extended:false}))
app.post('/addbook',(req,res)=>{
    //在服务端，可以通过 req.body 来获取 JSON 格式的表单数据和 url-encoded格式的数据
    console.log(req.body)
    res.send('ok')  
})
```

### 5、第三方的中间件

```JavaScript
非expres官方内置的，由第三方开发的就是第三方中间件
例、在 express@4.16.0 之前的版本中，经常使用 body-parser 这个第三方中间件，来解析请求数据，
使用步骤、
1、运行 npn install body-parser 安装中间件
2、使用require导入中间件
3、调用 app.use()注册并使用中间件
//注意 express内置的 express.urlencoded 中间件，就是基于body-parser 这个第三方中间件进一步封装出来的
```

### 自定义中间件

```JavaScript
模拟 express.urlencoded 这个中间件 来解析POST提交的表单数据
步骤
1、定义中间件
2、监听req的data事件
3、监听req的end事件
4、使用querystring模块解析请求体数据
5、将解析出来的数据对象挂载为req.body

示例、
//解析查询字符串的自定义函数
const qs = require('querystring')
// 1、定义
const bodyParse = (req,res,next)=>{
    //2、监听req的data事件
    let str = ''
    req.on('data',(chuck)=>{
        str += chuck
    })
    //3、监听req的end事件 (请求体发送完毕后自动触发)
    req.on('end',()=>{
        //4、 调用 qs.parse() 解析查询字符串
        const body = qs.parse(str)
        //5、 将解析出来的请求对象，挂载为req.body属性
        req.body = body     
        next()
    })
}
// 把封装好的解析请求体函数暴露出去
module.exports = bodyParse
```

## 使用express写接口

```JavaScript
1、服务器页面
const express = require('express')
const app = express()
//配置解析表单数据的中间件	来解析post请求体里面的数据
app.use(express.urlencoded({extended:false}))

// 导入api路由接口
const router = require('./16.router')
//挂载为为全局中间件
app.use('/api',router)
//启动服务器
app.listen(80,()=>{
    console.log('server is runing at http://127.0.0.1');
})

2、接口页面
const express = require('express')
const router = express.Router()
//挂载路由
router.get('/get',(req,res)=>{
    // 通过req.query 方法获取客户端通过查询字符串，发送过来的数据
    const query = req.query
    res.send({
        status:0,   //0处理成功 1处理失败
        message:'请求 GET 成功',    //请求状态描述
        data:query  //响应给客户端的数据
    })
})
//定义post接口
router.post('/pot',(req,res)=>{
    // 通过req.body获取请求体种包含 url-encoded格式的数据
    const body = req.body
    //调用res.send()方法，向客户端响应结果
    res.send({
        status:0,
        message:'请求 POST 成功',
        data:body  
    })
})
//向外暴露接口
module.exports = router
```

### 接口的跨域问题

```JavaScript
刚才编写的接口，有跨域问题，不支持跨域请求
解决接口跨域问题的方案主要有两种
CORS(主流的解决方案，推荐使用)
JSONP(有缺陷，只支持get请求)
```

### 使用CORS中间件解决跨域问题

```JavaScript
core是express的一个第三方中间件，通过安装和配置cors中间件，可以很方便的解决跨域问题
使用步骤
1、运行 npm install cors 	// 安装中间件
2、使用 const cors = require('cors')	//导入中间件
3、在路由之前调用 app.use(cors())	//配置中间件
```

### 什么是CORS和注意点

```JavaScript
CORS(跨域资源请求)是一系列HTTP响应体组成，这些HTTP响应头决定浏览器是否阻止前端JS代码跨域获取资源
浏览器的同源安全策略默认会阻止网页，跨域 请求资源，但如果接口服务器配置了 CORS 相关的HTTP响应头，就可以解除浏览器端的跨域访问限制

// CORS注意事项
1、CORS 主要在服务器端进行配置，客户端浏览器无须做任何额外的配置，即可请求开启了 CORS 接口
2、CORS在浏览器有兼容性，只有支持XMLHttpRequest Level2 的浏览器，才能正常访问开启了 CORS 的服务端接口(IE10、Chorme4+、FireFox3.5+)
```

### CORS响应头部

```JavaScript
1、Access-Control-Allow-Origin
响应头部可以携带一个 Access-Control-Allow-Origin : origin 字段
其中 origin 参数的值制定了允许访问该资源的外域URL
res.serHeader('Access-Control-Allow-Origin','*')	//* 表示允许来自任何域的请求
res.serHeader('Access-Control-Allow-Origin','http://127.0.0.1')		//设置只允许 http://127.0.0.1 的请求才能访问

2、Access-Control-Allow-Headers
默认情况下，cors仅支持客户端向服务器发送如下9个请求头
Accept,Accept-Language、Content-Language、DPR、Downlink、Save-Data、Viewport-Width、Width、Content-Type 	(允许增加的值仅限于，text/plain、multipart/form-data、application/x-www-form-urlencoded)
// 增加新的请求头 示例、
允许客户端向服务器发送 Content-Type 请求头和 x-www-form-urlencoded
注意 	多个请求头之间用英文的逗号分隔
res.serHeader('Access-Control-Allow-Headers','Content-Type,x-www-form-urlencoded)
              
3、Access-Control-Allow-Methods
默认情况下，cors仅支持客户端发起的 post，get，head 请求
// 增加新的或全部
res.serHeader('Access-Control-Allow-Methods','POST.GET,HEAD')	//只允许 POST.GET,HEAD 请求
res.serHeader('Access-Control-Allow-Methods','*')	//允许所有的请求
```

### JSONP接口

```JavaScript
1、创建JSONP接口的注意事项
如果在项目中已经配置了cors跨域资源共享，为了防止冲突，必须配置cors中间件之前声明的 JSONP 的接口，否则 JSONP 接口会被处理成开了cors的接口
示例、
// 优先创建 JSONP 接口(这个接口不会被处理成 cors 接口)
app.get('api/jsonp',(req,res)=>{})
// 在配置cors 中间件
```

