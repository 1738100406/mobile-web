



































#  一、移动web开发之流式布局

小tips

![](https://vi2.xiu123.cn/live/2020/07/01/17/1003v1593595095516160140.jpg)



立即执行函数 沙箱函数

opacity 透明度

![](https://vi3.xiu123.cn/live/2020/07/01/18/1003v1593599096789943139.jpg)

把箭头看到contener外后  要对箭头进行	**子绝父相**









## >视口

视口( viewport )就是浏览器显示页面内容的屏幕区域。视口可以分为**布局视口**、 **视觉视口**和**理想视口**

## 2.1布局视口layout viewport

+ 一般移动设备的浏览器都默认设置了一 个布局视口,用于解决早期的PC端页面在手机上显示的问题。
+ iOS, Android基本都将这个视口分辨率设置为980px ,所以PC上的网页大多都能在手机上呈现,只不
过元素看上去很小, -般默认可以通过手动缩放网页。

## 2.2视觉视口visual viewport
+ 字面意思, 它是用户正在看到的网站的区域。注意:是网站的区域。
+ 我们可以通过缩放去操作视觉视口 ,但不会影响布局视口,布局视口仍保持原来的宽度。

## 2.3理想视口ideal viewport ★
+ 为了使网站在移动端有最理想的浏览和阅读宽度而设定
+ 理想视口,对设备来讲,是最理想的视口尺对
+ 需要手动添写meta视口标签通知浏览器操作
+ meta视口标签的主要目的:布局视口的宽度应该与理想视口的宽度一致,简单理解就是设备有多宽,我
们布局的视口就多宽

##  2.4总结
+ 视口就是浏览器显示顽面内容的屏幕区域
视口分为布局视口、视觉视口和理想视口
+ 我们移动端布局想要的是理想视C就是手机屏幕有多宽,我们的布局视C ]就有多宽
+ 想要理想视口 ,我们需要给我们的移动端页面添加meta视口标签

## 2.5 meta视口标签标准写法：

<meta name="viewport" content="width=device-width,
initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0,user-scalable=no">
<meta http-equiv="X-UA-Compatible" content="ie=edge">
```
body {
    min-width: 320px;
	max-width: 540px;
    width: 15rem; /*=750/50*/ 
    margin: 0 auto;
    line-height: 1.5;
    font-family: Arial,Helvetica ;
    background: #F2F2F2;
}
```




| 属性          | 解释说明                                          |
| ------------- | ------------------------------------------------- |
| width         | 宽度设置的是viewport的宽度,可以设置为device-width |
| initial-scale | 初始化缩放比,大于0的数字                          |
| maximum-scale              | 最大缩放比,大于0的数字 |
| minimum-scale | 最小缩放比,大于0的数字 |
| user-scalable | 用户是否可以缩放yes或no(1或0) |

## >二倍图

## 3.1物理像素&物理像素比
+ PC端 和早前的手机屏幕/普通手机屏幕: 1CSS像素= 1物理像素的
+ Retina (视网膜屏幕)是一种显示技术,可以将把更多的物理像素点压缩至一块屏幕里，
从而达到更高的分辨率,并提高屏幕显示的细腻程度。

## 3.2多倍图
+ 对于一张50px* 50px的图片,在手机Retina屏中打开,按照刚才的物理像素比会放大倍数,这样会造成图片模糊

+ 在标准的viewport设置中,使用倍图来提高图片质量,解决在高清设备中的模糊问题

+ 通常使用二_倍图,因为iPhone 6\7\8的影响，但是现在还存在3倍图4倍图的情况,这个看实际开发公司需求

+ 背景图片注意缩放问题

## 3.3背景缩放background-size
background-size属性规定背景图像的尺寸
background-size:背景图片宽度背景图片高度;
单位:		长度|百分比Icover Icontain;
+ cover		把背景图像扩 展至足够大,以使背景图像完全覆盖背景区域。
+ contain		把图像图像扩展至最大尺寸,以使其宽度和高度完全适应内容区域

## 3.4多倍图切图cutterman

![](https://vi0.xiu123.cn/live/2020/06/27/14/1003v1593240377613676067.jpg)

```
二倍精灵图做法
+ 在firework里面把精灵图等比例缩放为原来的一半
+ 之后根据大小测量坐标
+ 注意代码里面background-size也要写 :精灵图原来宽度的-半
```



## 移动端开发选择

## 4.1移动端主流方案
1.单独制作**移动端**页面(主流)				2.**响应式**页面兼容移动端(其次)

京东商城手机版										三星手机官网
淘宝触屏版												...
苏宁易购手机版
....

三星电子官网: www.samsung.com/cn/ , 通过判断屏幕宽度来改变样式,以适应不同终端。
缺点:制作麻烦，需要花很大精力去调兼容性问题

## 4.2总结
现在市场常见的移动端开发有单独制作移动端页面和响应式页面两种方案
现在市场主流的选择还是单独制作移动端页面

## 移动端技术解决方案
## 5.1移动端浏览器
移动端浏览器基本以webkit内核为主,因此我们就考虑webkit兼容性问题。
我们可以放心使用H5标签和CSS3样式。
同时我们浏览器的私有前缀我们只需要考虑添加webkit即可
![](https://cdn.u1.huluxia.com/g4/M01/8A/70/rBAAdl727YGAGdHhAAF-tncwlfM608.png)

## 5.2 CSS初始化normalize.css
移动端CSS初始化推荐使用 normalize.css/
+ Normalize.css :保护了有价值的默认值
+ Normalize.css :修复了浏览器的bug
+ Normalize.css :是模块化的
+ Normalize.css :拥有详细的文档
官网地址: http://necolas.github.io/normalize.css

## 5.3 CSS3盒子模型box-sizing

+ 传统模式宽度计算 :

  盒子宽度= CSS中设置的width + border + padding

+ CSS3盒子模型: **box-sizing:border-box;**

  宽度= CSS中设置的宽度width 里面包含了border和padding

>>也就是说,我们的CSS3中的盒子模型，padding和border不会撑大盒子了

```
				传统or CSS3盒子模型?
>移动端可以全部CSS3子模型
>PC端如果完全需要兼容N我们就用传统模式,如果不考虑兼容性,我们就选择CSS3盒子模型
```

## 6.移动端常见布局

移动端布局和以前我们学习的PC端有所区别:

1.单独制作移动端页面(主流)							2.响应式页面兼容移动端(其次)

流式布局 (百分比布局)							     媒体查询
flex弹性布局 (强烈推荐)								bootstarp
less + rem+媒体查询布局
混合布局

## 6.1流式布局(百分比布局)
+ 流式布局, 就是百分比布局,也称非固定像素布局。
+ 通过盒子 的宽度设置成百分比来根据屏幕的宽度来进行伸缩,受固定像素的限制,内容向两侧填充。
+ 流式布局方式是移动web开发使用的比较常 见的布局方式。

![](https://cdn.u1.huluxia.com/g4/M03/8A/80/rBAAdl7287eAEllCAAAR6IahTU0772.png)

max-width最大宽度( max-height最大高度)
min-width最小宽度 ( min-height最小高度)

# 二、移动web开发之flex布局

## 2.1布局原理
flex是flexible Box的缩写,为弹性布局" ,用来为盒状模型提供最大的灵活性,任何一个容器都可以指定为flex布局。

当我们为父盒子设为flex布局以后,元素的float、clear 和vertical-align属性将失效。
	

![](https://cdn.u1.huluxia.com/g4/M02/8C/16/rBAAdl738a6AdTl1AAFxhXpO8w8136.png)

	**总结flex布局原理:**
	就是通过给父盒子添加flex属性,来控制子盒子的位置和排列方式
##  3.1常见父项属性
以下由6个属性是对父元素设置的

+ flex-direction :设置主轴的方向

+ justify-content :设置主轴上的子元素排列方式
+ flex-wrap :设置子元素是否换行
+ align-content :设置侧轴上的子元素的排列方式(多行)
+ align-items :设置侧轴上的子元素排列方式(单行)
+ flex-flow :复合属性,相当于同时设置了flex-direction和flex-wrap

## 3.2 flex-direction设置主轴的方向★

| 属性值         | 说明           |
| -------------- | -------------- |
| row            | 默认值从左到右 |
| column         | 从上到下       |
| row-reverse    | 从右到左       |
| column-reverse | 从下到上       |



## 3.3 justify-content设置主轴.上的子元素排列方式★
注意:使用这个属性之前一定要确定好主轴是哪个

| 属性值             | 说明                                        |
| ------------------ | ------------------------------------------- |
| flex- start        | 默认值从头部开始如果主轴是x轴，则从左到右   |
| flex-end           | 从尾部开始排列                              |
| **center**         | **在主轴居中对齐(如果主轴是x轴则水平居中)** |
| **space- around**  | **平分剩余空间**                            |
| **space- between** | **先两边贴边再平分剩余空间(重要)**          |

## 3.4 flex-wrap设置子元素是否换行★
默认情况下,项目都排在一条线( 又称心轴线”) 上。flex-wrap属性定义 , flex布局中默认是不换行的。

| 属性值 | 说明          |
| ------ | ------------- |
| nowrap | 默认值,不换行 |
| wrap   | 换行          |

## 3.5 align-items设置侧轴上的子元素排列方式(单行)★
该属性是控制子项在侧轴(默认是y轴)上的排列方式在**子项为单项**的时候使用

| 属性值     | 说明                       |
| ---------- | -------------------------- |
| flex-start | 默认值从上到下             |
| flex-end   | 从下到上                   |
| **center** | **挤在一起居中(垂直居中**) |
| stretch    | 拉伸                       |

## 3.6 align-content 设置侧轴.上的子元素的排列方式(多行)
设置子项在侧轴上的排列方式并且只能用于**子项出现换行**的情况(条行) , **在单行下是没有效果的。**

| 属性值        | 说明                                  |
| ------------- | ------------------------------------- |
| flex-start    | 默认值在侧轴的头部开始排列            |
| flex-end      | 在侧轴的尾部开始排列                  |
| center        | 在侧轴中间显示                        |
| space-around  | 子项在侧轴平分剩余空间                |
| space-between | 子项在侧轴先分布在两头,再平分剩余空间 |
| stretch       | 设置子项元素高度平分父元素高度        |



## align-content和align-items区别
align-items适用于单行情况下，只有上对齐、下对齐、 居中和拉伸
align-content 适应于换行(多行)的情况下(单行情况下无效) , 可以设置上对齐、下对齐、 居中、拉伸以及平均分配剩余空间等属性值。

总结就是单行找align-items多行找align-content

![](https://cdn.u1.huluxia.com/g4/M03/8C/28/rBAAdl73_CqATTcjAAD3yRhXjpA046.png)

## 3.7 flex-flow
flex-flow属性是flex-direction和flex-wrap属性的复合属性
flex- flow: row wrap;

## 4.1 flex 属性★
flex属性定义子项目分配剩余空间,用flex来表示占多少份数。

```javascript
. item {
		flex: 1 /* default 0 */
}
```

## 4.2 align-self控制子项自己在侧轴.上的排列方式
align-self属性允许单个项目有与其他项目不一样的对齐方式,可覆盖align-items属性。默认值为auto ,表示继承父元素的align- items属性,如果没有父元素,则等同于stretch.

```javascript
span:nth-child(2) {
		align-self: flex-end;/*设置自己在侧轴上的排列方式*/
}
```

## 4.3 order属性定义项目的排列顺序
数值越小,排列越靠前,默认为0.
注意:和z-index不一样。

![](https://cdn.u1.huluxia.com/g4/M03/8C/C1/rBAAdl74VXaASD7eAAGt0HLIaTw371.png)



# 三、移动web开发之rem布局

## 1.rem单位
rem (root em)是一个相对单位 ,类似于em , em是元素字体大小。
不同的是rem的基准是相对于html元素的字体大小。
比如,根元素( html )设置font-size= 12px;非根元素设置width:2rem;则换成px表示就是24px。

## 2.什么是媒体查询
媒体查询( Media Query )是CSS3新语法。
●使用 @media查询,可以针对不同的媒体类型定义不同的样式
●@media 可以针对不同的屏幕尺寸设置不同的样式
●当你重置浏览器大小的过程中.页面也会根据浏览器的宽度和高度重新渲染页面
目前针对很多苹果手机、Android手机 ,平板等设备都用得到多媒体查询
```
    @media screen and (min-width: 320px) {
        html{
            font-size: 18px;
        }
    }
    
    div{
        height: 1rem;
        font-size: 0.6rem;
        background-color: pink;
    }
```


## 3. Less基础
## 3.1维护css的弊端
CSS是一门非程序式语言,没有变量、函数、SCOPE (作用域)等概念。
●CSS需要书写大量看似没有逻辑的代码. CSS冗余度是比较高的。
●不方便维护及扩展,不利于复用。
●CSS没有很好的计算能力
●非前端开发工程师来讲,往往会因为缺少CSS编写经验而很难写出组织良好且易于维护的CSS代码项目。

## 3.3Less使用
我们首先新建一个后缀名为less的文件 ，在这个less文件里面书写less语句。
●Less 变量
●Less编译
●Less嵌套
●Less运算

## 3.4 Less变量
变量是指没有固定的值,可以改变的。因为我们CSS中的一些颜色和数值等经常使用。
@变量名:值;
1.变量命名规范
●必须有@为前缀
●不能包含特殊字符  不能以数字开头
●大小写敏感

## 3.5 Less嵌套
如果遇见(交集|伪类|伪元素选择器)
●内层选择器的前面没有 &符号,则它被解析为父选择器的后代;
●如果有&符号,它就被解析为元素自身或父元素的伪类。

```css
a:hover{
	color: red;
}
```

Less嵌套写法
```css
a{
   &:hover{
    	color: red;
   }
}
```

## 3.7 Less运算★
注意：
●乘号 (*)  和除号 (/ ) 的写法
●运算符中间左右有个空格隔开 1px  +  5
●对于两个不同的单位的值之间的运算,运算结果的值取第一个值的单位
●如果两个值之间只有一个值有单位,则运算结果就取**第一个**单位

## 4.rem适配方案技术使用(市场主流)
技术方案1										技术方案2 (推荐)
●less												flexible.js
●媒体查询										●rem
●rem

总结:
1.两种方案现在都存在。
2.方案2更简单,现阶段大家无需了解里面的js代码。

## 4.1rem实际开发适配方案1
rem +媒体查询+ less技术
  1.设计稿常见尺寸宽度


| 设备       | 常见宽度                                                   |
| ---------- | ---------------------------------------------------------- |
| iphone 4.5 | 640px                                                      |
| iphone 678 | 750px                                                      |
| Android    | 320px、360px、 375px、 384px、 400px、 414px 500px、 720px |

   一般情况下 ,我们以一套或两套效果图适应大部分的屏幕,放弃极端屏或对其优雅降级, 牺牲-些效果
   **现在基本以750为准**

## 4.2.动态设置html标签font-size大小
①假设设计稿是750px
②假设我们把整个屏幕划分为15等份(划分标准不一可以是20份也可以是 10等份)
③每一份作为html字体大小 ,这里就是50px
④那么在320px设备的时候.字体大小为320/15就是21.33px
⑤用我们页面元素的大小除以不同的html字体大小会发现他们比例还是相同的
⑥比如我们以750为标准设计稿
⑦一个100*100像素的页面元素在750屏幕下，就是100/ 50转换为rem是2rem * 2 rem比例是1比1 
⑧320屏幕下，html 字体大小为21.33则2rem = 42.66px 此时宽和高都是42.66 但是宽和高的比例还是1比1
⑨但是已经能实现不同屏幕下页面元索盒子等比例缩放的效果

## 4.3.元素大小取值方法
①最后的公式:页面元素的rem值=页面元素值(px) / ( 屏幕宽度1划分的份数)
②屏幕宽度/划分的份数就是html font- size的大小.
③或者:页面元素的rem值=页面元素值( px) / html font-size字体大小

## 4.4.设置公共common.less文件
1.新建common.less 设置好 最常见的屏幕尺寸,利用媒体查询设置不同的html字体大小,因为除了首页其他页面也需要
2.我们关心的尺寸有320px、360px、 375px、 384px、 400px、 414px、 424px、 480px、 540px、 720px、 750px
3.划分的份数我们定为15等份
4.因为我们pc端也可以打开我们苏宁移动端首页,我们默认htm字体大小为50px ,注意这句话写到最上面

## 5.新建index.less文件引入
1.新建index.less 这里面写首页的样式
2.将刚才设置好的common.less引入到index.less里面语法如下:

@import ”common”//在index.less 中导入common.less文件

3.生成index.css引入到index.html里面



# VSCode px 转换rem插件**cssrem**
这是一个神奇的插件**cssrem**

![](https://vi2.xiu123.cn/live/2020/06/30/15/1003v1593502822322586754.jpg)

这个插件默认的html文字大小 cssroot 16px=1rem 可修改为其他

![](https://cdn.u1.huluxia.com/g4/M03/91/45/rBAAdl767lmAb0NQAAE179xQOMA226.png)

# 1.响应式开发
## 1.1响应式开发原理
就是使用媒体查询针对不同宽度的设备进行布局和样式的设置,从而适配不同设备的目的。

![](https://cdn.u1.huluxia.com/g4/M02/91/64/rBAAdl76_3eAb4GaAAFj_2LduGE947.png)

超小屏幕(手机,小于768px) : 设置宽度为100%
小屏幕(平板，大于等于768px) : 设置宽度为750px
中等屏幕(桌面显示器,大于等于992px) :宽度设置为970px
大屏幕(大桌面显示器，大于等于1200px) : 宽度设置为1170px

## 2.Bootstrap

Bootstrap来洎Twitter (推特) , 是目前最受欢迎的前端框架。Bootstrap 是基于HTML、CSS和JAVASCRIPT的，它简洁灵活,使得**Web开发更加快捷**。

## 2.1优点
●标准化的html + cs编码规范
●提供了一套简洁、直观、强悍的组件
●有自己的生态圈,不断的更新迭代
●让开发更简单,提高了开发的效率

## 2.2版本
●2.x.x:停止维护,兼容性好，代码不够简洁,功能不够完善。
●3.x.x:目前使用最多稳定,但是放弃了IE6-IE7。对IE8支持但是界面效果不好,偏向用于开发响应式布局、移动设备优先的WEB项目。
●4.x.x :最新版,目前还不是很流行

## 2.3 Bootstrap使用
在现阶段我们还没有接触JS相关课程,所以我们只考虑使用它的样式库。
Bootstrap使用四步曲: 

1. 创建文件夹结构
2. 创建html骨架结构
3. 引入相关样式文件
4. 书写内容

## 2.4.创建html骨架结构

```html
    <meta name="viewport" content="width=device-width,user-scalable=no,
    initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
    <!--要求当前网页使用IE浏览器最高版本的内核来渲染 -->
    <meta http-equiv="X-UA-Compatible" content="IE=edge">

    <!-- Bootstrap -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/css/bootstrap.min.css" rel="stylesheet">

    <!-- HTML5 shim 和 Respond.js 是为了让 IE8 支持 HTML5 元素和媒体查询（media queries）功能 -->
    <!-- 警告：通过 file:// 协议（就是直接将 html 页面拖拽到浏览器中）访问页面时 Respond.js 不起作用 -->
    <!--[if lt IE 9]>
      <script src="https://cdn.jsdelivr.net/npm/html5shiv@3.7.3/dist/html5shiv.min.js"></script>
      <script src="https://cdn.jsdelivr.net/npm/respond.js@1.4.2/dest/respond.min.js"></script>
    <![endif]-->
```
## 2.5书写内容
> 直接拿Bootstrap 预先定义好的样式来使用
> 修改Bootstrap原来的样式,注意权重问题
> 学好Bootstrap的关键在于知道它定义了哪些样式,以及这些样式能实现什么样的效果

## 2.6.布局容器
Bootstrap需要为页面内容和栅格系统包裹一个.container容器, Bootstarp预先定义好了这个类,叫.container
它提供了两个作此用处的类。

1. container类
●响应式布局的容器 固定宽度
●大屏( >=1200px)宽度定为1170px
●中屏( >=992px)宽度定为*970px
●小屏(>=768px) 宽度定为750px
●超小屏 (100%)

2. container-fluid类
●流式布局容器 百分百宽度
●占据全部视口 ( viewport )的容器。
●适合于单独做移动端开发

## 3.栅格系统简介
栅格系统英文为"gridsystems" ,也有人翻译为“网格系统”, 它是指将页面布局划分为等宽的列,然后通
过列数的定义来模块化页面布局。
Bootstrap提供了一套响应式、 移动设备优先的流式栅格系统,随着屏幕或视口( viewport )尺寸的增加,系统会自动分为最多**12列**。
Bootstrap里面container宽度是固定的,但是不同屏幕下, container的宽度不同,我们再把container,划分为**12等份**

## 3.2栅格选项参数
栅格系统用于通过一系列的行 ( row )与列( column )的组合来创建页面布局,你的内容就可以放入这些创建好的布局中。

![](https://vi2.xiu123.cn/live/2020/06/30/20/1003v1593520087621133883.jpg)

●行 ( row )必须放到container布局容器里面
●我们实现列的平均划分需要给列添加类前缀
●xs-extra small :超小; sm-small :小; md-medium: 中等; lg-large :大
●列( column)大于12,多余的“列( column)"所在的元素将被作为一个整体另起-行排列
●每**一列默认有左右15像素的padding**
●可以同时为一列指定多个设备的类名，以便划分不同份数例如class= "col-md-4 col-sm-6"

## 3.3列嵌套
栅格系统内置的栅格系统将内容再次嵌套。简单理解就是一个列内再分成若 干份小列。我们可以通过添加一个新的row元素和一系列.col-sm-*元素到E经存在的.col-sm-*元素内。

![](https://vi2.xiu123.cn/live/2020/06/30/22/1003v1593526148493167010.jpg)

我们列嵌套最好加1个行row这样可以取消父元素的padding值而且高度自动和父级-样高

```
<!--列嵌套-->
<div class="col-sm-4">
    <div class="row">
        <div class="co1- sm-6">小列</div>
        <div class="co1-sm-6">小列</div>
    </div>
</div>

```

## 3.4响应式工具
为了加快对移动设备友好的页面开发工作,利用媒体查询功能,并使用这些工具类可以方便的针对不同设备
展示或隐藏页面内容。

![](https://cdn.u1.huluxia.com/g4/M02/92/2F/rBAAdl77S7GANnYbAAGGAowe5lE421.png)

**与之相反的,是visible- xS visible-sm visible-md visible-lg**是显示某个页面内容

●流式布局(百分比布局)
**●flex弹性布局(推荐)**
**●rem适配布局(推荐)**
●响应式布局
建议:我们选取一种主要技术选型，其他技术做为辅助,这种混合技术开发
































