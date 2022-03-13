# css的定位和动画

## 一.定位

1.背景色：background

如果是border-box盒子，给里面加入background属性时，此时颜色范围在border+内边距+content的区域。

2.一个div的分层

文字内容在做上面，下来是浮动元素，之后是块级子元素，下来是边框，最下面是背景元素。

文字内容（最上面）

浮动元素（第二层）

块级子元素（第三层）

边框（第四层）

背景属性（最下面 ）

3.position

属性与属性值

(1)static：一般是默认值，不写

(2)relative:相对定位，升起来，但不脱离文档流

(3)absolute:绝对定位，相对于relative的定位（相对于祖先元素最近的一个定位元素，就是非static）,脱离原来位置，另起一层。

(4)fixed：固定定位，固定在视口界面某一位置。

(5)sticked：粘滞定位，粘在一个地方不走。

注意：

a.默认情况下，z-index的属性值是auto,不创建新层叠上下文，比其他多1，就会压住其他盒子。0/1/2/-1/-2

b.关键点:

```css
white-space: nowrap; //不准换行
```

c.**用absolute和fixed,一定要写上top/left**，top :0;right 0;否则有些阅览器，会出现位置错乱。

d.善用left:50%;加负margin

5.层叠上下文

只要使用了定位属性元素，默认就会在所有元素的最上面，之后在z-index变为正数，会在更上面进行叠加。

也可以将z-index变为负数，就会在不断往下面覆盖。

## 二.动画

### 1.定义

由许多静止的画面(帧)，以一定的速度(如每秒30张)连续播放时，肉眼因视觉残象产生错觉，而误以为是活动的画面。

### 2.概念

帧：每个静止的画面都叫做帧

播放速度：每秒24帧（影视）或者30帧（游戏）

### 3.渲染

a.过程

根据HTml构建HTML树(DOM)

根据CSS构建CSS树（CSSOM）

将两棵树合并成一颗渲染树（render tree）

Layout布局（文档流，盒模型，计算大小，和位置）

Paint绘制（把边框颜色，文字颜色，阴影等画出来）

Compose合成（根据层叠关系展示画面）

b.更新样式

一般采用JS来更新样式

三种更新模式

全走:javascript->style->Layout->paint->composite

跳过layout:javascript->style->paint->composite

跳过layout和paint:javascript->style->composite

c.因为CSS属性会触发哪个流程，不确定，所以可以登录一个网站，上面会把属性的渲染都告诉。

```http
http://csstrigers.com/
```

d.CSS渲染过程依次包括布局，绘制合成

e.CSS动画优化

JS优化:使用requestAnimationFrame代替setTimeout或setIinterval

CSS优化：使用will-change或translate

### 4.transform

a.四个常用功能

位移：translate

```
transform:translateX(50px);//X方向移动
transform:translateY(50px);//y方向移动
transform:translate(50px.50px);//合并
transform:translateZ(50px);//z方向移动
```



其中Z方向需注意是建立在三维世界中，使用这个属性必须给其父元素加一个属性**perspective:1000px,**

之后这个动画会向着父元素的视点移动变化。

注意：用transform进行居中

```css
left:50%;

top:50%;

transform:translate (-50%,-50%);
//绝对居中
```

缩放：scale

```
transform:scale(1.5); //缩放为自己大小的1.5倍
```

也支持x,y方向上的缩放。

旋转：rotate

```css
transfrom : roate(45deg); //顺时针旋转45度
```



倾斜：skew

```css
transform: skewX(15deg);//沿x周倾斜15度
```

b.使用transform经验

1.一般都需要配合transition过渡,加一个时间：**all 1s**

2.inline元素不支持transform,需要先变成block

3.上面的四个属性可以组合使用

例：

```css
transform:scale(1.2)  roate(45deg);
```

### 5.transition过渡

a.作用：补充中间帧

b.语法：

transition:属性名 时长 过渡方式 延迟

```css
transition:left 200ms linear;
```

可以用逗号分隔两个不同属性

```
transition:left 200ms, top 400ms;
```

可以用all代表所有属性

```css
transition:all 200ms
```

注意：

1.display：none =》block没法过渡

一般改为visibility :hidden =>visible

2.过渡必须要有起始。

### 6.animation

1.两种方法

a.使用两次transform

.a===transform ===> .b

.b ===transform ===> .c

2.animation
a.过程
(1)先声明关键帧  @keyframes.xxx{    }
(2)添加动画
(3)让动画停在最后一帧：可以加入一个forwards

b.keyframes完整语法

(1)

```css
@keyframes slidenin {
from {
transform:translateX(0％);
}
to {
transform:translateX(100%);
}
}
```

(2)

```css
@keyframes identifier {
0% {  top:0; left:0; }
30%{  top:50px; }
68%,72%{ left:50px; }
100%{ top:100px;left:100%;}
}
```

c.animation语法
**animation:时长|过渡方式|延迟|次数|方向|填充模式|是否暂停|动画名;**
时长:1s或1000ms

过渡方式:跟transition取值一样，如linear

次数:3或2或者infinite(不停的)

方向:reverse(相反)|alternate(交替的)|alternate–reverse

填充模式:none|forwards(停到末尾，不返回)

是否暂停:paused|running(继续)
