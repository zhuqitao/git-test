---
title: 日常开发常用的css小技巧总结
date: 2017-12-05 21:16:24
tags:
    - css
---

## css黑科技 ##

 **currentColor当前颜色**

```
<a href="##" class="link"><i class="icon"></i>返回</a>
.icon {
  display: inline-block;
  width: 16px; 
  height: 20px;
  background-image: url(http:jartto.wang/test.png);
  background-color: currentColor; /* 该颜色控制图标的颜色 */
  background-position: 0 0;
}
.link:hover {
  color: #333; /* 虽然改变的是文字颜色，但是图标颜色也一起变化了 */
}
```

 **vh、vw、vmin、vmax单位**
浏览器的视口的宽、高被分为100份，1vh相当于浏览器高度的百分之一，即浏览器的高度为800px,则1vh=8px。
vw宽度同理。vh、vw支持calc算法

```
.box{
  height: calc(100vh - 50px);
}
h1 {
  font-size: 8vw;
}
```
vmin和vmax是与这次宽度和高度的最大值或最小值有关，取决于哪个更大和更小。例如，如果浏览器设置为
1100px宽、700px高，1vmin会是7px,1vmax为11px。然而，如果宽度设置为800px，高度设置为1080px，
1vmin将会等于8px而1vmax将会是10.8px。

```
.box{
  height: calc(100vmax - 50px);
}
```

 **边框多个颜色**

```
.box{
    border-style:solid;
    border-color:red green blue pink;
}
```
必须设置border-style才会有效果

 **css画小箭头**
使用border和transparent属性实现

```
/*箭头向上*/
.arrow-up {
  width:0;
  height:0;
  border-left:30px solid transparent;
  border-right:30px solid transparent;
  border-bottom:30px solid #fff;
}
/*箭头向下*/
.arrow-down {
  width:0;
  height:0;
  border-left:20px solid transparent;
  border-right:20px solid transparent;
  border-top:20px solid #0066cc;
}
```

 **图片滤镜效果**
使用filter属性可以实现各种各样的图片效果，包括以下属性

```
grayscale 灰度
sepia 褐色
saturate 饱和度
hue-rotate 色相旋转
invert 反色
opacity 透明度
brightness 亮度
contrast 对比度
blur 模糊
drop-shadow 阴影
```

 **浏览器滚动条美化（仅支持webkit内核浏览器）**

```
/*滚动条 start*/
::-webkit-scrollbar {
  width: 1px;
  height: 4px;
  background-color: #F5F5F5;
}
/*定义滚动条轨道 内阴影+圆角*/
::-webkit-scrollbar-track {
  box-shadow: inset 0 0 6px rgba(0,0,0,0.3);
  background: #fff ;
}
/*定义滑块 内阴影+圆角*/
::-webkit-scrollbar-thumb {
  border-radius: 3px;
  box-shadow: inset 0 0 6px rgba(0,0,0,.3);
  // background-color:rgba(7, 170, 247, 0.7);
  background-color: transparent;
}
::-webkit-scrollbar-thumb:hover {
  border-radius: 3px;
  box-shadow: inset 0 0 6px rgba(0,0,0,.3);
  background-color:rgba(7, 170, 247, 1);
}
```

 **使用 :not() 在菜单上应用/取消应用边框**

```
.nav li:not(:last-child) {
  border-right: 1px solid #666;
}
```

 **浏览器默认行高line-height一般为1.15倍，可以给body设置line-height:1来设置行高为1.0倍**

```
body{
      line-height: 1;
}
```

 **使用负的 nth-child 选择项目**
在CSS中使用负的 nth-child 选择项目1到项目n。
```
li {
  display: none;
}
li:nth-child(-n+3) {
  display: block;
}
```
 **禁用鼠标事件**

```
.disabled {
    pointer-events: none;
}
```

