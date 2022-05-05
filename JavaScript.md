#   JavaScript

### 基础知识

书写位置

写在</body>的上面

输入输出语句

```js
1、write	写到页面
document.write("我愿意")
document.write("<h1>我愿意</h1>")	也可以识别标签
2、alert	提示框
alert("我愿意")
3、console	控制台
console.log("我愿意")
4、prompt	输入语句
prompt("我愿意")
```

##### 变量

```js
声明
let	变量名		以后声明变量都用let
赋值
let age = 18；
把18的数值给到age
输出变量
console.log(age)
规则
1、字母严格区分大小写
2、只能用下划线、字母、数字、$,且数字不能开头
规范
1、遵守小驼峰命名法，后面每个单词首字母大写	如userName
```



##### 数据类型

```js
基本数字类型
number	数字型
string	字符串型	通过'',"",包含的，推荐使用 ''
boolean	布尔型		两个值	true false
undefined	未定义型
null	空类型
undefined 和 null的区别
1、undefined表示没有赋值
2、null表示赋值了，但是内容为空
引用数据类型
object	对象	
function	函数
array	数组
JavaScript是弱数据类型，变量属于那种类型，只有赋值之后才能知道;

字符串拼接
利用 + 做拼接	console.log('我是'+'pink')
也可也实现字符串加变量的拼接
let age = 18
console.log('我的年龄'+age)
console.log('我今年'+age+'岁啦')
```

##### 检测数据类型

```js
typeof 关键字
typeof 数据
会返回该数据的数据类型
```

##### 类型转换

```js
隐式转换	系统内部的转换
+ 号只要两边有一个是字符串，都会把另外一个转换为字符串
除了 + 号以外的算数运算符 - * / ;等都会把数据转换为数字类型
 + 号作为正号解析可卡因转换成number
例、let num = '10';
console.log(+num)	此时的'10'会变为数字类型
```

###### 转换为数字型

```JavaScript
Number{数据}	

parseInt()	
转换为数字型，只保留整数，没有四舍五入
parseInt('10.999')	转换为10

parseFloat()
转换为数字型，会保留小数
parseFloat('10.999')	转换为10.999

区别
Number()	只能放数字类型的字符，否则返回NaN
parseFloat()
1、可以接受任意类型的值，但只保留数字
2、经常用于过滤单位	例、parseFloat('100px')	过滤后只保留100
```

###### 转换为字符型

```JavaScript
String()
toString()方法	(2)如果里面是2则转换为2进制	很少用
```



##### 模板字符串

```JavaScript
符号 ``
document.write(`我今年${age}岁啦`)
用反引号包括的字符串里面可以直接写	${age}	来包裹变量
```

### 流程控制

##### 运算符

```JavaScript
算数运算符
+ 加 - 减 * 乘 / 除 % 取模（余数）	取模在开发中经常作为某个数字是否被整除
优先级	先乘除，后加减 有括号先算括号

赋值运算符
= 将等号右边的值赋予给左边，要求左边必须是一个变量
+=	num = 18	num +=1 此时num = 19
+= -= *= /=	都是为了简化代码

一元运算符
++	自增 1	-- 自减 1		经常用来计数使用
++i 前自增	先自加 在运算		i++ 后自增 先使用 后自加

比较运算符
>	左边是否大于右边
<	左边是否小于右边
>=	左边是否大于等于右边
<=	左边是否小于等于右边
==	左右两边是否相等
===	左右两边是否类型和值都相等	以后判断要用===	开发常用
!==	左右两边是否不全等
比较运算符的结果为	true 或 false

逻辑运算符
&&	逻辑与	符号两边都为true，结果才为true	一假则假
||	逻辑或 符号两边有一个true，就为true	一真则真
！	逻辑非	true 变 false false 变 true 真变假	假变真

逻辑运算符中的短路
&&	左边为false则短路		例、console.log(false&&20)	因为&&一假则假，当判断到之左边为 false 时那么后边就不在执行
||	左边为true则短路		例、console.log(true&&20)		因为||是一真则真，当判断到左边为 true 时则后面的不在执行
五个当false来看的值
false	数字0	''	undefined null
常用短路来判断用户输入为空的时候赋值为0
let num prompt('请输入一个数字')
num = num || 0;

此时当用户输入为空时	由于''值为false因此执行后面的	所以num的值会赋值为0
```

##### if分支语句

```JavaScript
单分支
if(条件){
    满足条件执行的代码
}
双分支
if(条件){
    满足条件执行的代码
}else{
    不满足条件执行的代码
}
多分支	可以无限写条件
if(条件1){
    满足条件执行的代码
}else(条件2){
    满足条件执行的代码
}else{
    不满足条件执行的代码
}
```

##### 三元运算符

```JavaScript
条件 ? 满足条件执行的代码 : 不满足条件执行的代码
常用来取最大值
let num1 = 20;
let num2 = 30;
let re = num1 > num2 ? num1 : num2
此时re会获取到最大值
```

##### switch语句

```JavaScript
switch case 语句一般用于等值判断不适合区间判断
switch case 一般要配合break关键字使用，没有break会造成case穿透
switch(数据){
    case 值1:
        代码1
        break
    case 值2:
        代码2
        break
    default:
        代码n
        break
}
例、
switch(1){
   case 1:
      alert(1)
      break
   case 2:
      alert(2)
      break
   case 3:
      alert(3)
      break
   default:
      alert('没有值')
}
```

##### while循环

```JavaScript
while(循环条件){
    要重复执行的代码(循环体)
}
判断条件是否为真，为真执行代码，执行完，返回判断，如果为真则继续执行，直到条件为假则结束循环
循环三要素
1、变量起始值
let i=1
2、终止条件(没有终止条件，循环会一直执行，早成死循环)
while(i<=10){
    document.write('月薪过万')
    3、变量变化值(用自增或者自减)
    i++
}
```

##### for循环

```JavaScript
for(声明记录循环次数的变量;循环条件;变化值){
    循环体
}
for(let i =1;i<=10;i++){
    documemt.write('月薪过万')
}
for 最大的价值是循环数组
数组名.length	可以获取到数组的长度
let arr = [1,2,3,4,5]
arr.length	此时的长度是5

循环嵌套
for(外部声明记录循环次数的变量; 循环条件; 变化值){
    for(内部声明记录循环次数的变量; 循环条件; 变化值){
        循环体
    }
}
外层循环执行一次，内部循环执行全部
for(let i=1;i<6;i++){	//外层行
    for(let j=1;j<=i;j++){	//内层列
       document.write(`⭐`)
   }
    document.write('<br>')
}
for(let i=1;i<=9;i++){	//乘法表
   for(let j=1;j<=i;j++){
       document.write(`${i} * ${j} = ${i*j} `)
   }
   document.write('<br>')
}
```

##### for和while区别

1、当明确循环的次数时用for

2、当不明确循环的次数时用while

##### 循环退出

```JavaScript
continue:	结束本次循环，继续下次循环
break:	退出所在的循环
```

### 数组

```JavaScript
声明
let 数组名 = [数据1，数据2，...，数组n]
取值
数组名[下标]
arr[0]	此时会取出arr数组中的第一个元素

获取到最大值
let arr = [2,6,1,77,52,25,7]
let max = arr[0]  //初始化第一个值为数组的第一个元素
for(let i =0;i<arr.length;i++){   //遍历数组
   if(max<arr[i+1]){       //当我的max不是最大值时，把最大值给max，始终保持最大值给到max
     max = arr[i+1]
   }
}
document.write(max)
```

##### 操作数组

###### 查，改

```
let arr = ['pink','hotpink','deeppink']
1、查
console.log(arr[0])		此时查询到数组下表的第0个元素	pink
2、改
arr[0] = 'lightpink'
console.log(arr[0])		此时数组内下标为0的元素被改为	lightpink
```

###### 增

```JavaScript
后添加
数组名.push()	方法将一个或多个元素添加到数组的末尾，并返回该数组的新长度
arr.push(元素1, ... ,元素n)

找出数组中的最大值添加到新数组
let arr = [2,0,6,1,77,0,52,0,25,7]
     let brr = []
     for(let i=0;i<arr.length;i++){
         if(arr[i]>=10){
             brr.push(arr[i])
         }
     }
document.write(brr)

前添加
数组.unshift()	方法将一个或多个元素添加到数组的前面，并返回该数组的新长度
arr.unshift(元素1, ... ,元素n) 
```

###### 删

```JavaScript
删最后
数组.pop()	方法从数组中删除最后一个元素，并返回该元素的值
arr.pop()

删第一个
数组.shift()	方法从数组中删除第一个元素，并返回该元素的值
arr.shift()

删除指定元素
数组.splice()	方法，删除指定元素
arr.splice(起始位置,删除几个元素)
1、起始位置是	指定修改的开始位置
2、删除几个元素是	表示要移除元素的个数，如果省略则默认从起始位置删到最后
```

### 算法

##### 冒泡排序

```JavaScript
let arr = [5,4,3,2,1]
let temp;
for(let i = 0 ;i<arr.length-1;i++){ //外层控制循环次数  只需要循环四次就可以    因此是arr.length-1
   for(let j =0;j<arr.length-i-1;j++){ //内层控制交换次数  交换次数随着交换逐渐减少    因此是arr.length-i-1
        if(arr[j]>arr[j+1]){
           temp = arr[j+1]     //把小值给到中间变量
           arr[j+1]=arr[j]     //把大值给到后面的位置
           arr[j] = temp       //把小值给到前面的位置
      }
   }
}
```

### 函数

```JavaScript
声明	一次声明可以多次调用
function 函数名(){
	函数体
}
function sayHai(){
    document.write('你好~~~')
}
调用函数
函数名()
sayHai()	会执行函数体里的内容	输出你好~~~
```

##### 函数传参

```JavaScript
function 函数名(参数列表){		
    函数体
}
参数列表可以有一个或多个，也可以没有
调用函数
函数名(传递的参数列表)
参数列表有几个则传递的参数列表也要对应的有几个
例、带有参数的函数
function getSum(参数1,参数2,...){
    document.write(num1+num2)
}
function getSum(num1,num2){	参数用	, 隔开
    document.write(num1+num2)
}
getSum(2,3)

形参: 声明函数时写在函数名右边小括号里的叫形参(形式上的参数)	此时 num1,num2 为形参
实参: 调用函数时写在函数名右边小括号里的叫实参(实际上的参数)	调用的时候getSum(2,3)这两个值为实参
```

##### 函数传参小技巧

```JavaScript
调用的时候会有个内部判断是否有参数传递进来
没有参数则 执行 x = 0
有参数则进行参数赋值
function fn(x=0,y=0){
    console.log(x+t)
}
fn()
fn(1,2)
```



##### 函数中逻辑中断

```JavaScript
getSum(x,y){
	x = x || 0
	y = y || 0
	document.write(x + y)
}
getSum()
通过逻辑中断来实现，当用户没有传递参数时赋值为0
当没有传参时	此时x和y的值会赋予为undefined
在函数里进行赋值时，||运算符大于 赋值运算符 = 因此先算 x || 0 但此时x和y的值为undefined 是false 在或运算中会直接把后面的值给x和y，因此就把0的值赋给了x和y
```

##### 函数的返回值

```JavaScript
作用
函数执行后得到的结果，结果是调用者想要的(函数内部不需要输出结果，而是返回结果)对程序的扩展性更高

当函数需要返回数据出去时，用 return 关键字
语法
return 数据

例、
function getSum(x,y){
	x = x || 0
	y = y || 0
	return x + y	return会把x+y的值给getSum(x,y)	也就是getSum(2,3) = 5
}
let total = getSum(2,3)		因为函数名可能会很长，所以我们习惯于用一个变量来接受函数的返回值
document.write(total)

函数的小细节
1、函数内部只能出现一次return，并且return后面的代码不会在执行
2、return后面的数据不要换行
3、函数可以没有return，没有的话默认返回值为undefined 

return返回多个值
我们可以利用数组来让return有返回多个值的功能
function getSum(x,y){
   let add = x+y
   let less = x-y
   return [add,less]	使用数组后就可以接收两个返回值了，也可以是多个
}
let total = getSum(1,2)
document.write(`第一个值为${total[0]},第二个值为${total[1]}`)
```

##### 传参函数示例

```JavaScript
1、传递数组元素
function getSum(arr) {
   let sum = 0;
   for (let i = 0; i < arr.length; i++) {
      sum += arr[i];
   }
   document.write(sum);
}
getSum([99, 98, 100]);
2、返回任意两个数中的最大值
function getMaxTwo(x,y){
   return x>y?x:y;
}
let two = getMaxTwo(5,10)
document.write(two)
2.1、返回最大值时，实参也可以放变量
let num1 = +prompt('请输入第一个数')
let num2 = +prompt('请输入第二个数')
function getMax(x,y){
   /*	返回值也可以有多个，但要在判断条件下，且只能执行一个return
   if(x>y){
        return x
    }else{
        return y
    }
    */
   return x>y?x:y
}
let Max = getMax(num1,num2)
document.write(Max)
3、计算输入的时分秒
let num = +prompt("请输入你要转换的时间");
function getTime(T) {
   let h = parseInt((T / 60 / 60) % 24);     //计算时
   let f = parseInt((T / 60) % 60);
   let m = parseInt(T % 60);
   h = h<10?`0${h}`:h
   f = f<10?`0${f}`:f
   m = m<10?`0${m}`:m
   //return [h, f, m];
   return `计算后的时间为${h}时${f}分${m}秒`
}
let Time = getTime(num);
document.write(Time)
//document.write(`${num} 转换为 ${Time[0]}时 ${Time[1]}分 ${Time[2]}秒`);
```

##### 匿名函数

```JavaScript
语法
let 变量名 = function(){
    //函数体
}
let fn = function(x,y){
    //函数体
}
调用
fn(1,2)
```

立即执行函数

```JavaScript
避免全局变量之间的污染
不需要调用 立即执行
//方式1
1、第一个小括号放的是形参，第二个小括号放的是实参
(function (x,y) {	//形参
    console.log(x+y)
})(1,2);	//实参
(function () {
    console.log(11)
}());

多个立即执行函数之间必须加 ; 隔开 不然会报错
所以立即执行函数后面最好加一个 ;
```



### 作用域

```JavaScript
1、函数的作用域
作用域是指可用性的代码范围
全局作用域
作用于所以代码执行的环境(整个script标签内部)或者一个独立的js文件

局部作用域
作用域函数内的代码环境，就是局部作用域，因为跟函数有关系，所以也称函数作用域

块作用域
块作用域用 {} 包括，if语句和for语句的{}等

2、变量的作用域
全局变量
函数外部let的变量
全局变量在任何区域都可以修改

局部变量
函数内部let的变量
局部变量只能在当前函数内部访问和修改
function fu(){
    let num = 10	该变量是局部变量，只在当前函数体内有用
}
function fn(){		函数内套函数，子函数可以访问到父函数的变量
    let num = 10
    function fn1(){	
        console.log(num)
    }
    fn1()	
}

块级变量
{}内部的let变量
let定义的变量，只能在块级作用域里访问，不能跨块访问，也不能跨函数访问

变量的特殊情况
变量有一个坑，特殊情况
如果函数内部或者块级作用域内部，变量没有声明，直接赋值，也会当全局变量看，但是强烈不推荐使用
但是有一种情况，函数内部的形参可以看做是局部变量

作用域链
当在不同作用域有重名变量时，使用变量会采用就近原则
let num = 10
function fn(){
    let num = 20	
    console.log(num)	优先查找函数体内部的num
}
fn()	此时会输出20
```

### 对象

```JavaScript
对象(object)也是一种数据类型，可以理解是一种无序的数据集合
```

##### 声明

```JavaScript
声明
let 对象名 = {}

let 对象名 = {
	属性名:属性值,
	方法名:函数
}
例、描述一个人的姓名、身高、年龄
let person = {
    uname:'andy',
    age:18,
    sex:'男'
}
多个属性之间用 , 分隔

对象是有属性和方法组成的，那么属性和方法都要写在对象里面
let person = {
    //属性
    uname:'pink',
    //方法	方法名:function(){}
    sayHi:function(){}
}
```

##### 访问属性

```JavaScript
对象属性使用
1、对象.属性名
2、对象['属性名']	必须加 ''
例
let goods = {
    name:'小米10青春版',
    num: 100012816024,
    weight:'0.55kg',
    address:'中国大陆'
}
console.log(goods.name)
console.log(goods['num'])
```

##### 访问方法

```JavaScript
let person = {
    name:'andy',
    sayHi:function(){		匿名函数
        document.write('hi~~~')
    },
    sum:function(x,y){		本质还是一个函数可以传递参数进来
       return x+y 
    }
} 
访问方式
对象.方法名()
person.sayHi()
person.sum(1,2)		传递实参
```

##### 操作对象

```JavaScript
查
对象.属性
对象['属性']

改
对象.属性=新值
let obj = {
    name:'',
    age:18
}
obj.age = 21	修改对象的值

 增
 对象.新属性名=新值
 let obj = {
    name:'',
    age:18
}
obj.sex='男'		新增属性
obj.sing = function(){		新增方法
    
}
1、增加新属性或方法	JavaScript可以非常方便的动态新增属性或方法
2、会去对象里查找是否有sex这个属性，如果有则更改属性值，如果没有则增加新属性

删
delete 对象名.属性名
一般很少删除对象
```

##### 遍历对象

```JavaScript
遍历对象需要用到新的语句
for in 循环语句
for(let k in obj){
    console.log(obj[k])
}
例
let obj = {
    name:'小明',
    age:18,
    sex:'男'
}
语法	遍历
for(let k in 对象名){	重点
    console.log(k)		//k是变量 得到的是带字符串的属性名
    console.log(obj[k])		//属性值
	//为什么这么写
     k === 'name' === 'age' ==='sex'
     k里面存的是变量，因此可以用obj[k]来获取到属性值
}
```

##### 数组对象

```JavaScript
数组里面可以放任何的数据类型
数组对象
let students = [
    { name: "小明", age: 18, gender: "男", hometown: "河北省" },
    { name: "小红", age: 18, gender: "女", hometown: "河南省" },
    { name: "小岗", age: 18, gender: "男", hometown: "山西省" },
    { name: "小丽", age: 18, gender: "女", hometown: "山东省" },
];
打印对象，起始里面的每一个对象都是，数组里面的元素
for (let i = 0; i < students.length; i++) {
   console.log(students[i].name);	.属性能拿到里面的值
}
```

##### 内置对象

Math数学对象

```JavaScript
random() 生成0-1之间的随机数(包括0不包括1)
ceil() 向上取整
floor() 向下取整
round()	就近取整(.5往大取整)
max() 找最大数
min() 找最小数
pow() 幂运算
abs() 绝对值

Matn.PI		//圆周率
Matn.random()
/*
返回一个随机数 是0-1之间的，但是是有小数值的
我们常用
(parseInt(Math.random()*10)		来对其进行取整	*10则返回0-9之间的
*/
Matn.ceil(1.1)	Matn.ceil(1.5)	//向上取整 会返回 2

Matn.floor(1.1)	Matn.floor(1.5)	//向下取整 会返回 1

Matn.round(1.1)	Matn.round(1.6)	//就近取整	会返回 1 和 2 (特殊情况1.5会往2取 -1.5会往-1取)
Math.max(1,7,9)		返回几个数值中的最大值，值可以是多个
Math.min(1,7,9)		返回几个数值中的最小值，值可以是多个
```

###### 求随机数公式

```JavaScript
1、生成一个1-10之间的随机数
let random1 = Math.floor(Math.random()*(10-1+1)+1)
2、生成一个Min-Max之间的随机数
Math.floor(Matn.random()*(Nax - Min + 1)+Max)
随机数函数
function getRandom(min,max){
   return Math.floor(Math.random()*(max-min-1)+min)
}
```

