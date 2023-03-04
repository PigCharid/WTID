# 语法

每一个键值属性对是用封号;隔开

# 选择器

选择器是通过样式属性来定位到html元素，css选择器的写法还是需要比较的熟悉

## 简单选择器

元素选择器、类选择器、id选择器和通用选择器

## 组合选择器

根据特殊的组合关系选中

### 后代选择器

空格，标识前面元素的所有后代，可以隔代

### 子选择器

大于号，只能是后代儿子

### 相邻兄弟选择器

加号，相邻还得是兄弟，不相邻也不行

### 通用兄弟选择器

波浪号，只要是对应的兄弟就行



## 伪类选择器

一个冒号，主要就是获取不同元素的不同状态下

### 链接

链接有几个伪类：link、visited、hover、active

### 一般元素

可以设置一个元素悬停再让一个元素出现

### :first-child

### 伪类

所有的伪类还蛮多的，先说几个常用的

悬停、聚焦、第n个孩子



## 伪元素选择器

双冒号，这个内容不多

::afeter y

::before

::first-letter

::first-line

::section 元素下选中的部分



## 属性选择器

选择带有特定属性的元素

比如选中a链接下有target属性值的元素

还有设定选取特定属性的值

对于不带class或者id的表单来说，属性选择器还蛮有优势的

### 选择元素有特殊属性的元素

### 选择元素有特殊属性带有特殊属性值的元素

### 属性值里面=特殊值的元素

### 属性值以什么开头的元素 |=

top-aaa

### 属性值以什么开头的元素 ^=

top-aaa + topaaa

### 属性值以什么结尾的元素

top-aaa + topaaa

### 选择元素有特殊属性带有特殊属性值的元素



# 使用方式

外部、内部、行内



# 颜色

## HEX

## RGB

好像有个rgba可以设置透明度

## HSL

hsla最后一个参数可以设置透明度



# 圆角

通过css的border-radius属性，可以实现任何元素的"圆角样式"

border-radius其实是四个属性的值`border-top-left-ridus` `border-top-right-ridus` `border-bottom-left-ridus` `border-bottom-left-ridus`的值，如果需要某一个角是圆角，就会用的上

border-radius也可以进行简写，对角理论，从左上角开始，顺时针

## 椭圆圆角

没有特定的椭圆的标签，能通过元素的框高和圆度的大小来控制，用百分比控制可以做出椭圆



# 边框图像

没很看懂

应该是把图像作为边框



# 背景

背景的属性蛮多的

## 背景颜色

### 透明度

opacity可以调整元素的透明度

rgba的最后一个参数也是调整透明度的



## 背景图片

需要用url把图片的路径给包装一下



## 背景重复

### 背景不重复

```
background-repeat: no-repeat;
```

### 背景水平重复

```
background-repeat: repeat-x;
```

### 背景垂直重复

```
background-repeat: repeat-y;
```

## 背景附着

设置背景是滚动的还是固定的

### 背景固定

```
background-attachment: fixed;
```

### 背景滚动

```
background-attachment: scroll;
```



# 边框

border允许您指定元素边框的样式、宽度和颜色

## 边框样式

`border-style`

- `dotted` - 定义点线边框
- `dashed` - 定义虚线边框
- `solid` - 定义实线边框
- `double` - 定义双边框
- `groove` - 定义 3D 坡口边框。效果取决于 border-color 值
- `ridge` - 定义 3D 脊线边框。效果取决于 border-color 值
- `inset` - 定义 3D inset 边框。效果取决于 border-color 值
- `outset` - 定义 3D outset 边框。效果取决于 border-color 值
- `none` - 定义无边框
- `hidden` - 定义隐藏边框



## 边框高度

就是边框的宽度，可以用像素去指定

`border-width`

## 边框颜色

`border-corlor`

## 边框各边

上下左右都可以单独设置

```
  border-top-
  border-right-
  border-bottom-
  border-left-
```



## 外边距

外边距可以设置以下的值：

- auto - 浏览器来计算外边距
- *length* - 以 px、pt、cm 等单位指定外边距
- % - 指定以包含元素宽度的百分比计的外边距
- inherit - 指定应从父元素继承外边距

允许负值

上下左右的属性可以简写，上、右、下、左



可以将 margin 属性设置为 `auto`，以使元素在其容器中水平居中，父类要是没有宽度，那么就没办法移动



### 外边距合并

