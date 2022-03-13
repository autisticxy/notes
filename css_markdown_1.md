## CSS基础笔记1



## 一、引入CSS的三种方式

### 1.通过link标签引入

例：

```html
<link rel="stylesheet" href="index.css">
```

rel:定义外部资源与文档的关系；链接样式表。其中"stylesheet"是定义一个外部加载的样式表。

href:被链接文档的位置(url)，就是外部资源文件名和文件路径。

### 2.直接在style 标签里书写样式

例：

```css
<style>
   p {
        color:red;
    }
</style>
```

### 3.内联样式

例：

```html
<p style="color: red;">CSS</p>
```

style：在后面进行编辑样式。

## 二.CSS语法

### 1.选择器里：

**选择器 {**

**属性1:值1;**

**属性2:值2;**

**}**

### 2.直接在body里面:

```css
body {

color :red;

font-size:14px;

}
```

### 3.at语法

@charset "UTF-8";

@import url(2.css);

@media(min-width:100px) and (max-width:200px)  {

语法1

}

## 三.常见选择器

### 1.标签选择器：

将选中所有的这个标签进行统一样式。

例：

```css
p {

color:red;

}
```

### 2.id选择器：

仅选中id一样的元素进行统一样式。

例：

```css
#id {

font-size :13px;

}
```

### 3.类选择器：

选中所有class是一样的元素进行统一样式。

例：

```css
. name {

border:1px solid  red;

}
```

注意：类选择器编辑时：前面要加一个  **.** 符号。

### 4.后代选择器：

外层标签写在外面，内层标签写在后面。进行嵌套的统一样式。

例：

```css
ul li {

line-height :1.4;

}
```

注意：**ul是父级，li是子级，其中li可以是任何基础标签，只要是后代，ul也可以是别的标签。**

### 5.子选择器：

只能选择作为元素最近一级的元素，进行统一样式。

例：

```css
div > p {

padding :10px;

}
```

注：**p标签必须是挨着父选择器最近的一个，也只改变这个，其他不行。**

6.并集选择器：

可以选择多组标签，中间用,隔开，为他们定义相同样式。

例：

```css
ul , div {

background : #888;

}
```

### 7.排序选择器：

相同的类名的选择器，用数字排序分别加样式，第一个和最后一个比较特殊；

```css
.item:first-child {   font-size :20px; }

.item:nth-child(2) {   color :red; }

.item:nth-child(3) {   font-size :30px; }

.item:nth-child(4) {   color :blue; }

.item:last-child {   font-size :20px; }
```



## 四.常见的样式文本属性

### a.字体属性

(1)字体大小：font-size

```css
p {    font-size :20px;             }
```

(2)字体样式：font-family

```css
 p {     font-family : "微软雅黑或者Miscorft YaHei"
 }
```

(3)字体粗细：font-weight

```css
p  {   font-weight: bold;     }
```

(4)字体风格： font-style 

```css
p  {         font-style: normal        }
```

(5)字体的复合样式：可以把字体的属性总结起来写。

语法规则：

```css
 body {

font: font-style  font-weight  font-size/line-height  font-family  

 }
```

注意:使用font属性时，**必须按照上面顺序来写，并用空格隔开，有些属性可以省略，但font-size/line-heght , font-family属性必须有。**

### b.文本样式

(1)颜色 color

```css
div  {  color :red;  }
```

(2)对齐文本 text-align

```css
div {     text-align:center ;           }
```

(3)文本装饰 text-decoration

```css
div  {   text-decoration : underline;  }
```

(4)行间距  line-height

```css
div  {   line-height :30px;     }
```

(5)文本缩进  text-indet 

```css
p  {  text-indet: 2em ;    }
```

### c.盒样式

1.content-box和border-box两种盒模型：

content-box的width只含**content**,而border-box的width包含**文字内容和border，padding.**

2.属性与属性值

margin:页边空白；

border:盒边框大小；

padding:元素边框与元素内容之间的空间；

width/height:宽度/高度，不要写宽度高度百分之百；

例：

```css
div  {

margin :10px;

border : 1px;

padding:4px;

width:33px;

height:33px;

}
```

3.外边距(marign)合并

(1)合并：**父级盒子和子级盒子的marign合并**，

**两个相同级别盒子的margin合并**

外边距(margin)合并只在高度重合合并，宽度不会合并。

(2)如何阻止合并

a.父级和子级盒子合并用**padding /border**挡住

b.父级和子级盒子合并用**overflow：hidden**挡住

c.父级和子级盒子合并用**display:flex;** 挡住

d.两个相同级别盒子合并用**inline-block**消除

## 五.文档流，定位与浮动

### 1.文档流(Normal Flow)

(1)文档流概述

**块级(block)盒子(div盒子等)从上到下依次排开**

**行级(内联元素(inline)等)从左到右放满折行**

(2)文档流的三个盒子

a.**lnline元素不要设置宽度，它的宽度为内部inline元素的和。**

inilne元素的高度是由line-height间接决定的，是它的实际高度，跟它本身无关。

b.**block元素的宽度是默认的，可以进行设置**，不一定是百分之百的，但不要写宽度百分之百。

**block元素的高度是由内部文档流的元素决定，可以设置height.**

c.inline-block结合两个特点，可以设置width。

inline-block高度跟block类似，可以设置height.

注意：

a.**不要在inline元素里面写block元素，会发生渲染。**

b.**如果div里面什么都没有，没文档流，高度为零；但span的元素如果里面什么都没有，高度也是line-height**。

(3)溢出：overflow，文档内容超出容器设置的高度。

overflow的四个属性：auto(灵活设置),scroll(滚动),visible,hidden

### 2.定位(Position)

让元素改变默认的位置，按照定位的方式移动盒子。

定位=定位模式+边偏移

比如相互覆盖，或者相对窗口固定

- relative:**相对定位**，相对于自己来移动位置，**相对于它原来位置来说**，**不脱标**，继续保留原来位置，后面的盒子仍一标准流的方式对待他。
- static:静态定位，无定位
- absolute:**绝对定位**,**脱离标准文档流**，是以其**父或祖先中最近的定位元素**为参考，其他情况以阅览器为准定位。
- fixed:**固定定位**，脱离标准文档流，永远以阅览器窗口为参考，跟父元素无关，不随滚动条滚动，会改变元素的显示模式。
- sticky: **粘性定位**，随”正常“文档流而动，直到规定位置，之后”粘“在那里。

边偏移：top,bottom,left,right;

**常用套路：父级参考点position:relative ,需要绝对定位元素position:absolute****

例：

```css
. container {      

position : relative;

}

. child {

position : absolute;

left:10px;

top:10px;

z-index:1;

}
```

### 3.浮动

(1)有很多的布局效果，标准流没有办法完成，利用浮动完成布局，浮动可以改变元素标签的排列方式，所以，**多个块级元素横向排列找浮动**。

(2)float属性用于创建浮动框，将其移动到一边，直到左边缘或右边缘及包含块或另一个浮动框的边缘。

语法规则：

```css
选择器  {     float : 属性值 ；  }
```

属性值：none , left ,right;

(3)浮动特性：

a.浮动元素会脱离文档流（脱标），漂浮在上面。

b.浮动元素会一行内显示并且元素顶部对齐

c.浮动元素会具有行内块元素特性

d.浮动盒子不在保留原先的位置

e.一般布局网页的时候先用**标准流的父元素**排列上下位置，之后**内部子元素采取浮动排列左右位置**。

(4)清除浮动：

​    a. 由于父级盒子不方便给高度，子盒子浮动又不占位置，最后父级盒子高度为0，就会影响下面的标准流盒子。

b.  语法规则：

选择器 :  {     clear : 属性值 ；}

属性值：left ; right ; both;

策略：闭合浮动

c.额外标签法：会在**浮动元素末尾添加一个空的标签**，必须是个块级元素，例如：

```css
<div style=" clear : both "></div>
```

或者其他标签。

d.添加overflow法:**给父级添加overflow属性**，将其属性设置为**hidden**.auto,scroll。

e.after伪元素法：after方式是额外标签法的升级版，给父级元素添加。

f.双伪元素法：给父元素添加，是额外标签法的升级版。

## 六.布局

### (1)布局是什么

固定宽度布局，一般宽度为960/10000/1024px

不固定宽度布局，主要靠文档流的原理来布局，本来就是自适应的，不需要加额外的样式。

### (2)float布局

步骤：子元素加  **float: left和width**，此时，<u>在父元素上加 . clearfix</u>

css里的父元素里面：

```css
. clearfix:after {

content: ' ';

display: block;

clear:both;

}
```

注意：1.如果是块级元素，并且宽度是固定的，左右两边的auto直接会让我们居中。（**margin:0 auto;**)

2.平均分配布局是加入-margin的手段。

3.图片如果超出可视范围，用一句css样式:vertical-align:middle;

### (3)flex布局

1.基本相关概念：

container：容器   ； items :容器内部的东西

<u>**2.变成flex容器两种方式：**</u>

```css
.container {

display : flex ;     //第一种写法
    
 // display inline-flex;  这是第二种写法

}
```

<u>3.改变items流动的方向（主轴）</u>

**从左往右排：**

```css
.container {  flex-direction:row  ;}
```

从右往左排：

```css
.container {  flex-direction : row-reverse;}
```

**从上往下排：** 

```css
.container { flex-direction : column ;}
```

从下往上排： 

```css
.container {  flex-direction : column-reverse;}
```

<u>4.折行：</u>

**因为flex的排列的特点弹性盒，一直在一行排下去，压缩自己的长度。所以，要进行折行。**

**折行语句：**

```css
.container {  flex-wrap: wrap;  }
```

**注意，该句默认是不折行的：不折行的属性值是：nowrap**

5.主轴对齐方式

默认主轴是横轴；除非你改变了flex-direction方向

a.默认对齐（左对齐）:

```css
.container {  justify-content : flex-start; }
```

b.右对齐：

```css
.container { justify-content : flex-end; }
```

**<u>c.居中对齐：</u>**

```css
.container { justify-content: flex-center;}
```

**<u>d.靠两边其余居中对齐；</u>**

```css
.container { justify-content: flex-between;}
```

e.围绕对齐：

```css
.container { justify-content: flex-around; }
```

6.次轴对齐

默认次轴是纵轴时：

a.往次轴开始流动上对齐： 

```css
.container { align-items: flex-start ;}
```

<u>**b.往容器居中对齐：**</u>

```css
.container { align-items: center;  }
```

c.在次轴的流动的结尾对齐：

```css
.container { align-items: flex-end ;}
```

d.在次轴都按最高的item高度对齐：

```css
.container { align-items : stretch ;}
```

7.多行分配

a. 把多余的行高逐一向上分配：

```css
.container {  align-content: flex-start ; }
```

c.把多余的行高逐一向下分配：

```css
.container { align-content: flex-end ;  }  
```

c.把多余的行高逐一向中间的两边分配：

```css
.container {  align-content : center; }
```

8.items的属性

a.order（可以控制它在的盒子里的显示顺序）

```css
.item:first-child {  order:4;}

.item:nth-child(2) {   order:3; }

.item:nth-child(3) {   order:1;}

.item:nth-child(4) {   order:5; }

.item:last-child {   order:2; }
```

b.flex-grow:通过数字控制多余的地方属于自己就是占多大宽度；

```css
.item:first-child {  flex-grow:1;}

.item:nth-child(2) {   flex-grow:2;}

.item:nth-child(3) { flex-grow:2;  }

.item:last-child {   flex-grow:1;}
```

注意：默认为零时，就不会占地方。

c.flex-shrink:通过数字控制缩小的距离的程度（原始宽度收到威胁时）；

```css
.item:first-child {  flex-shrink:0;}

.item:nth-child(2) {   flex-shrink:1;}

.item:last-child {   flex-shrink:0;}
```

注意：当值为零时，缩小时，该items不缩小，默认是1，要缩都缩小。

d.b和c的缩写，不用加shrink；用空格隔开；第一个是grow的值，第二个是shrink的值，第三个是盒子的宽度。

```css
.item:first-child {  flex: 1 1 100px;}

.item:nth-child(2) {   flex : 1 2 100px;}

.item:last-child {   flex: 0 1 100px;}
```

e.单独让一个items对齐；(特立独行多出来)

```css
. items {  align-self: flex-start/flex-end; }
```

8.布局时的小技巧：

a.不要把width，和height写死，除非特殊说明

b.用min-width/max-width/min-height/max-height

c.flex和margin-left/right:auto；配合会有意外的效果。

### (4)grid布局

1.grid布局也分container和items，成为container的语法 ：

```css
. container {  display :grid  ；//变成grid的语法；

// inline-grid;         //变成inline-grid;

}
```

2.行和列

container父元素也称为新时代的表格

语法:

```css
.container {  grid-template-columns: 40px 50px auto 50px 40px ;

grid-template-rows: 25% 100px auto;

}
```

![1646291490936](1646291490936.png)

3.给item设置范围

```css
.item-a {

grid-column-start: 2;       //  给里面的items设置开始的线，列从2开始  

grid-column-end: five;      // 给里面的items设置结束的线，列从2开始

grid-row-start:row1-start;  //给里面的items设置开始的线，行从1开始

grid-row-end:3 ;                  //给里面的items设置开始的线，行从3结束

}
```

4.fr：平均分割

``` css
. container {

grid-template-columns: 1fr  1fr  1fr ;

}
```

5.分区grid-template-areas

```css
.container {

display : grid;

grid-template-columns:50px 50px 50px 50px ;

grid-template-rows: auto;

grid-template-areas:   //分区域，并加上区域名字

"header header header"

" aside  main  aside"

" footer  footer  footer ";

}

.item-a {

grid-area:header;

}

.item-b {

grid-area:main;

}

.item-c {

grid-area:aside;

}

.item-d {

grid-area:  footer;

}
```

6.设置空隙 grid-gap

```css
.container {

grid-column-gap:10px;  //跟每行设置间隙10

grid-row-gap:15px;   //给每列设置间隙15

}
```



## 七.css三大特性

### 1.层叠性

  **相同选择器**设置**相同样式**，此时一个样式就会覆盖另一个冲突的样式。

层叠性原则：

- ​      样式冲突，遵循原则是**就近原则**，哪个样式离结构近，就执行哪个样   式（覆盖了）

- ​     样式不冲突，不会层叠

  ### 2.继承性

  ​      子标签会继承父标签的某些样式

- ​      恰当地使用继承可以简化代码，降低CSS样式的复杂性

- ​      子元素可以继承父元素的样式(text-, font-,line-这些元素开头的可以继承，以及color属性)    

- ​      行高的继承性：

  ```css
  body {
  
  font : 12px/1.5  Microsoft YaHei ;
  
  }
  ```

  ​      注意：行高可以跟单位也可以不跟，1.5是相当于文字大小的倍数。**一般在body里写，行高写1.5，子元素可以根据文字大小自动调整行高。**

    

### 3.优先级

当同一个元素指定多个选择器，就会有优先级的产生。

  1. 选择器相同，会执行层叠性

  2. 选择器不同，则根据选择器权重执行

     | 选择器               | 选择器权重 |
     | -------------------- | ---------- |
     | 继承或者*            | 0,0,0,0    |
     | 元素选择器           | 0,0,0,1    |
     | 类选择器，伪类选择器 | 0,0,1,0    |
     | id选择器             | 0,1,0,0    |
     | 行内样式style=""     | 1,0,0,0    |

     注意：!important级别最高，**继承的权重为零，如果该元素没有直接选中，不管父元素权重多高，子元素得到的权重都是0。**

     c.权重叠加:如果是复合选择器，则会有权重叠加，需要计算权重（不会有进位）。

## 八.border调试法

用一个border语法来进行调试，来判断语句出错是在上面还是下面。

语句：**border: 2px solid red;**

先判断选择器是否正确，是否出现，之后在进行每个语句的对错，是否出现，即可调试，之后删除即可。

## 九.练习素材

### 1.PSD

Freepik搜索PSD web

中文免费的可以搜365psd里的UI套件还行

### 2.效果图

dribbble.com顶级设计师社区

用肉眼模仿它

### 3.去你经常去的网站进行模仿

### 4.画效果图-磨刀
