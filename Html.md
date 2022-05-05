# Html

### 知识细则

```css
1、如果一个行内标签有绝对定位,则改行内标签不需要在设置块元素也就是不需要在用 display : block 来设置块元素
span{
​	position: absolute;
}
2、最小高度，当高度大于时可以被撑开
min-hight:像素值	
```

2、选择多个li里的最后一个

```css
li:last-child
```

##### 缩放背景图

```css
图片等比例缩放，当高度或宽度和盒子尺寸相等，图片就不在缩放
background-size:contain;
图片完全覆盖到整个盒子，可能会导致图片显示不全
background-size:cover;
```

##### 弹性盒子省略号的显示

```html
<div class="goods">/*此时父级盒子已经有了	display:flex	属性*/
	<div class="pic">
		<a href="#"><img src="./uploads/clothes_goods_5.jpg" alt="" /></a>
	</div>
	<div class="text">
		<h5>拉夫劳伦T恤男正品圆领短袖拉夫劳伦T恤男正品圆领短袖</h5>
		<p>颜色：<span>白色</span> 尺码：<span>M</span> 数量<span>1</span></p>
	</div>
</div>
```

```css
.order .content li .goods .text{
    /*弹性盒子由于大小会被内容撑开，所以给其0的宽度
    但flex：1设置其宽度就能实现弹性盒子的隐藏省略*/
    width: 0;
    flex: 1;
}
.order .content li .goods .text h5{
    text-overflow: ellipsis;
    /*不换行*/
    white-space: nowrap;
    /*溢出隐藏*/
    overflow: hidden;
}
```

图标和文字之间的对齐

```css
vertical-align: middle;
给图标或文字任意一个添加该属性就能实现其对齐
```



## CSS

### 平面转换

transform属性

##### 位移

```css
transform:translate(水平移动距离，垂直移动距离)
/*两个数值可以取	px（像素）或 %（百分比）数值可正可负*/
绝对定位的位置居中
position: absolute;
left: 50%;
top: 50%;
transform: translate(-50%,-50%);/*使用该属性的-50%来实现*/
width: 100px;
height: 50px; 
可以用（-50%，-50%）来实现
```

##### 旋转

```css
transform:rotate(角度)	角度单位是deg	数值可正可负
正数顺时针转，负数逆时针转，选择可以改变坐标轴向
```

##### 旋转原点

```css
transform-origin:原点水平位置 原点垂直位置
该属性是复合属性，数值之间空格隔开
取值方位名词 left，top，right，bottom，center	像素单位的值
例、img{
    transition:all 2s;
    transform-origin: right bottom;/*改变旋转点至右下角*/
}img:hover{
    transform:rotate(360deg)
}

```

##### 缩放

```css
transform:scale(缩放倍数)
```

##### 渐变

```css
background-image:linear-gradient{
颜色1，颜色2
}
```

### 空间转换

在实际应用中3d的空间转换是很少使用的

##### 空间位移

```css
transform:translate3d(x,y,z)	取值可以正负（像素、百分比）
```

##### 透视

```css
perspective属性实现透视效果
该属性需要添加给父级元素才能有效果
建议数值800-1200之间的像素
```

##### 空间旋转

```css
transform:rotateZ()
transform:rotateX()
transform:rotateY()
```

##### 立体呈现

```css
transform-style:preserve-3d;
使子元素处于真正的3d空间
```

##### 空间缩放

```css
transform:scaleX(倍数)
transform:scaleY(倍数)
transform:scaleZ(倍数)
transform:scale3d(X,Y,Z)
```

### 动画

```css
animation
实现步骤
1、定义动画,两种定义方式，第二种值是可变的但最后要到100%
@keyframes{
    form{}
    to{}
}
百分比占的是动画总时长的百分比
@keyframes{
    0%{}
    25%{}
    50%{}
    100{}
}
2、使用动画	谁改变给谁添加动画
animation:动画名称 动画花费时长;
动画属性
animation:动画名称 动画时长 速度曲线 延迟时间 重复次数 动画方向 执行完毕时状态;
/*
动画名称和动画时长必须赋值
速度曲线 > steps（3）也可也用该属性来设置，它会把动画分成几等分执行,使用该属性可以实现逐帧动画
重复次数 > infinite 无限重复
动画方向 > alternate 往返方向
执行完毕状态 > forwards，停留在动画结束的状态
取值不分先后顺序
如果有两个时间值，则第一个表示动画时长，第二个表示延迟时间
*/
animation:
change 1s steps(12) infinite, 
run 5s forwards linear;
使用，分隔可以实现多个动画一起调用
动画暂停 > animation-play-state:paused;
```

## 移动端

##### flex布局

```css
父元素添加	display:flex;	子元素可以自动的挤压或拉伸
默认效果	子集横向排列	默认主轴在水平，弹性盒子都是沿主轴排列
```

##### 修改主轴方向

```css
flex-direction:column;	使子元素垂直排列
```

##### 对齐

1、先确定主轴方向	2、在选择对应的属性实现主轴或侧轴的对齐方式

##### 主轴对齐方式

```css
justify-content:值;
有六个值
center			沿主轴居中排列
space-around	弹性盒子沿主轴均匀排列，空白间距均匀分在弹性盒子两侧
space-between	弹性盒子沿主轴均匀排列，空白间距均分在相邻盒子之间
space-evenly	弹性盒子沿主轴均匀排列，弹性盒子与容器之间间距相等
```

##### 侧轴对齐方式

```css
align-items:值;
align-self:值;	控制某个弹性盒子在侧轴的对齐方式，要添加给对应的子集，添加给谁就控制谁的侧轴对齐方式，属性值与align-items一样
flex-start	默认值，起点开始依次排列
flex-end	终点开始依次排列
center		沿侧轴居中排列
stretch		默认值，弹性盒子沿着侧轴线被拉伸至铺满容器，注意、子集盒子如果有高度则不会拉伸，当子集高度没有时则会拉伸到父盒子的高度
```

伸缩比

```css
flex:值;	取值类型:数值(整数)	取值是占用父级剩余尺寸的份数
```

#####  弹性盒子换行

```css
flex-wrap:wrap;	子元素换行显示
align-content:值;	调整行对齐方式	取值与justif-content基本相同
```

## 移动适配

##### rem方案

```css
rem单位
相对单位	rem单位是相对于HTML标签的字号计算结果
1rem=1HTML字号大小
媒体查询检测视口宽度来设置不同的差异化字号
@media(媒体特性){
	选择器{
		css属性
	}
}
例、@media(width:320px){	width:320px就是窗口的宽度
	html{
		font-size:32px
	}
}

目前rem方案布局中，将网页分为10等分，html标签的字号为视口宽度的1/10既
视口宽度320px，则根字号为32px
@media(width:320px){	width:320px就是窗口的宽度
	html{
		font-size:32px
	}
}
rem适配原理
rem单位尺寸
1、确定设计稿对应的设备html标签字号
	查看设计稿宽度	确定参考设备宽度
2、rem单位的尺寸
	rem的单位尺寸=px单位数值/基准根字号
例、宽度68px	设计稿375px宽	html37.5宽
则rem = 68/37.5=1.813rem
高度29px	则rem = 29/37.5=0.773rem
```

##### rem自动适配和

```css
flexible.js	能根据不同视口宽度给html网页根节点设置不同的font-size
```

##### less语法

```css
less是一个css预处理器，less文件后缀是.less	扩充了css语言，使css具备一定的逻辑性、计算能力
浏览器不识别less代码，网页要引入对应生成的css文件

VsCode	Easy LESS插件	会保存less时自动生成css文件
less注释
单行注释	//	快捷键CTRL+/
块注释		/**/shift+alt+a	

less运算
加 减 乘 
可以直接写	width:100+100px;	width:100+100px;	width:10*10px;
除法要加小括号	width:(68 / 37.5rem);	width:68 ./ 37.5rem;

less嵌套	快速选择后代选择器
父级选择器{
    /*父级样式*/
    子级选择器{
        /*子级样式*/
    }
}
.father{
    color:red;
    .son{
        width:100px;
    }
}
对应生成css文件
.father{
    color:red;
}
.father .son{
    width:100px
}
&	表示当前选择器  
&在谁里面就是选择的谁
.father{
    color:red;
    .son{
        width:100px;
        &:hover{
            color:white;
        }
    }
}
此时对应的css文件会生成.son:hover{color:white;}、在那个括号里面就会选择到括号前的类名

less变量
存储数据，方便使用和修改
语法
定义变量:@变量名:值;
使用变量:css属性:@变量名;
例
@color:pink;
.box{
    color:@color;
}
.father{
    background-color:@color;
}
一个变量可以被多个使用

less导入
@:import 'base.less';
@:import 'index.css';

less插件设置css导出位置
在设置里搜easy	出现LESS:Compile	下的	在setting.json中编辑	添加代码
"less.compile":{
    "out": "../css/"	这是根路径，可以去设置位置
  }

单独导出路径
在该less文件的第一行写导出语句
// out: ./abc/	导出路径
// out: ./qqq/base.css	控制导出文件夹和css名字

less禁止导出
//out :false;
```

##### vm/vh方案新技术

```css
1、vw = 1/100视口宽度
2、vh = 1/100视口高度
vw/vh单位尺寸 = px单位数值 / (1/100视口宽度)
开发时只能单独使用一种尺寸，vw或vh，不能两个同时用
```

## 响应式网页

适合内容少，企业站布局

```css
媒体查询
/*判断视口宽度<=768改变背景色*/
@medis(max-width:768px){
    body{
        background-color:pink;
    }
}
/*判断视口宽度>=768改变背景色*/
@medis(min-width:768px){
    body{
        background-color:blue;
    }
}
所以的css属性都有层叠性
检测视口区间	要按顺序
min-width(从小到大)
max-width(从大到小)

link引入
两个媒体查询会判断当视口大于1200时使用上面的css样式，当大于798时用798时的样式
<link rel="stylesheet" href="./css/index.css" media="(min-width:1200px)" />
<link rel="stylesheet" href="./css/index.css" media="(min-width:798px)" />

媒体查询-隐藏
当不需要一些盒子时可以设置一定值对其进行隐藏
检测视口宽度小于768则隐藏left盒子
@medis(max-width:768px){
    left{
        dispaly:none;
    }
}
```

##### BootStrap

```css
引入
<link rel="stylesheet" href="./bootstrap-3.4.1-dist/css/bootstrap.css">
/*压缩过的bootstrap 文件更小，一般引入压缩过的*/
<link rel="stylesheet" href="./bootstrap-3.4.1-dist/css/bootstrap.min.css">
栅格系统
```

BootStrap3默认将网页分为12等份

|          | 超小屏幕 | 小屏幕   | 中等屏幕 | 大屏幕   |
| -------- | -------- | -------- | -------- | -------- |
| 响应断点 | <768px   | >=768px  | >=992px  | >=1200px |
| 容器宽度 | 100%     | 750px    | 970px    | 1170px   |
| 类前缀   | col-xs-* | col-sm-* | col-md-* | col-lg-* |

里面的*号就是要占的份数

如果是大屏占四个内容	则类为	col-lg-3	* =12/4 =3份

当使用分等份布局时，由于本身设置的大小已经是宽度的100%，没有多余的地方，因为在设置边距效果时，需要用内容来撑开，显示成有边距的效果，如下面在里面设置a标签给大小来实现间距，因为本身父div有15的padding间距

```html
 <div class="col-xs-12 col-sm-6 col-md-3"><a href="#">1</a></div>
            <div class="col-xs-12 col-sm-6 col-md-3"><a href="#">1</a></div>
            <div class="col-xs-12 col-sm-6 col-md-3"><a href="#">1</a></div>
            <div class="col-xs-12 col-sm-6 col-md-3"><a href="#">1</a></div>
```



##### BootStrap3类名

```css
.container	版心类名	自带左右各15的padding
如果不想要版心的左右padding	可以加一个.row来消除掉	也可也自己定义padding:0;来消除
.row类自带左右-15的padding	作用是抵消container的padding
<div class="container">
     <div class="row">  
		这样写来消除版心类的15px padding
     </div>
</div>
.container-fluid	定义一个宽100%的容器	自带左右15的padding

BootStrap3引入js文件时要引入两个
jQuery要首先引入在引入BootStrap的js文件
    <script src="./bootstrap-3.4.1-dist/js/jquery-1.9.1.min.js"></script>
    <script src="./bootstrap-3.4.1-dist/js/bootstrap.min.js"></script>
jQuery要首先引入在引入
```

## ifarme 标签

```html
iframe 元素会创建包含另外一个文档的内联框架
```

![iframe标签的用法](C:\Users\ME\Desktop\笔记\image\iframe标签的用法.png)
