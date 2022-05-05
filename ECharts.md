# ECharts

官网地址

```JavaScript
https://echarts.apache.org/zh/index.html
```

文档太多即查即用

### 基本使用

```JavaScript
1、下载并引入ECharts					//图标依赖于这个库
2、准备一个具备大小的DOM容器			//生成图表会放入该容器
3、初始化ECharts示例对象				//实例化ECharts对象
4、制定配置项和数据					//根据具体需求修改配置选择
5、将配置项设置给ECharts实例对象		//让ECharts对象根据修改好的配置生效

图表类型在官网可以选择，直接复制制定好的配置项和数据修改即可
```

### ECharts相关配置

```JavaScript
1、title:标题组件
2、tooltip:提示框组件
3、legend:图例组件
4、toolbox:工具栏
5、grid:直角坐标系内绘网格图
6、xAxis:直角坐标系grid(网格)中的x轴
7、yAxis:直角坐标系grid(网格)中的y轴
8、series:系列列表，每个系列通过type决定自己是什么样的图表类型(什么类型的图标)
8.1 type 类型
8.2	系列名称
8.3 stack数据堆叠	如果设置值相同，则会数据堆叠 //数据堆叠是: 第二个数据值，第一个数据值+第二个数据值
给stack设置不同值，或者直接去掉该属性则不会发生数据堆叠
9、color:调色盘颜色列表
```

### 边框图片

```
属性
border-image属性，这个属性
1、使用场景
盒子大小不一、但是边框样式相同、此时就需要边框图片来完成
2、边框图片的切图原理
把四个角切出去，中间部分可以横排、拉伸或者环绕
3、边框图片的语法规范
border-image-source			用在边框的图片路径
border-image-slice	图片边框向内偏移，(裁剪的尺寸，一定不加单位，上右下左顺序)
border-image-width	图片边框的宽度(需要加单位)(不是边框的宽度，是边框图片的宽度)
border-image-repeat	图片边框是否平铺(repeat)铺满(round)或拉伸(stretcg)默认拉伸
```

### 提示框组件	tooltip

```JavaScript
// 提示框组件
tooltip: {
	// trigger 触发方式。  非轴图形，使用item的意思是放到数据对应图形上触发提示
	trigger: 'item',
	// 格式化提示内容：
	// a 代表series系列图表名称  
	// b 代表series数据名称 data 里面的name    
	// c 代表series数据值 data 里面的value   
	formatter: "{a} <br/>{b} : {c} ({d}%)"
},
```

### 图标跟随浏览器变化一起改变

```JavaScript
//当浏览器缩放，图标一起缩放
//监听页面尺寸改变
window.addEventListener('resize',function(){
    //让图表调用resize这个方法
	myEcharts.resize()
})
```

