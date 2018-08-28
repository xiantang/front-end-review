# front-end-review
前端拾遗 突然有一天发现 woc 不会写css和html 就找了份Guide 撸一下
[MDN web doc](https://developer.mozilla.org/zh-CN/)

# CSS

### CSS是如何实现的    

当浏览器显示文档的时候
他必须将文档的内容和他的样式结合在一起     

    1. 浏览器将html和css转换成DOM对象DOM在计算机中表示文档    
    2. 浏览器显示DOM   


### CSS的新名词

* 属性(property):可以理解的标识符 例子:字体，宽度，背景颜色
* 属性值(value):表示你要把属性修改成什么样子

### CSS声明
![Alt text](https://mdn.mozillademos.org/files/3665/css%20syntax%20-%20declaration.png)
1. 如果你写错了属性值，声明将会无效，引擎会忽略掉他。
2. 使用美式拼写，不能打错别字

### CSS语句

```css
@import 'custom.css';
```
该@-规则向当前 CSS 导入其它 CSS 文件

```css 
@media (min-width: 801px) {
  body {
    margin: 0 auto;
    width: 800px;
  }
}
```
上述语句在规格大于801像素的情况下才会应用。

### 基本选择器
通用选择（*）是最终的王牌。它允许选择在一个页面中的所有元素。由于给每个元素应用同样的规则几乎没有什么实际价值，更常见的做法是与其他选择器结合使用(参考下面 组合 .)
```html
<html>
    <head>
        <meta charset="utf-8">
        <title>My Css experiment</title>
        <link rel="stylesheet" href="style.css">
    </head>
    <body>
        <div>
            <p>I think the containing box just needed
            a <strong>border</strong> or <em>something</em>,
            but this is getting <strong>out of hand</strong>!</p>
          </div>
    </body>
</html>
```

```css
*{
    padding: 5px;
    border: 1px solid black;
    background: rgba(255, 0, 0, 0.25)
}
```

### 存在和值属性选择器  
* [attr]: 改选择器包含attr的所有属性。  
* [attr=val]：该选择器仅选择 attr 属性被赋值为 val 的所有元素。
* [attr~=val]：元素的属性中还包含其他属性值，都会被应用红色的文本颜色

```html
    <ul>
      <li data-quantiy="1kg" data-vegetable>Tomatoes</li>
      <li data-quantiy="3" data-vegetable>Onions</li>
      <li data-quantity="25cl" data-vegetable="liquid">White wine</li>
      <li data-quantity="3" data-vegetable="spicy ">ite </li>
    </ul>
```

```css
[data-vegetable]{
    color: green;
}

[data-vegetable="liquid"] {
    background-color: goldenrod;
  }
  
  /* 所有具有"data-vegetable"属性且属性值包含"spicy"的元素，
  即使元素的属性中还包含其他属性值，都会被应用红色的文本颜色 */
  [data-vegetable~="spicy"] {
    color: red;
  } 
```  
NOTE:本例中的 data-* 属性被称为 数据属性。它们提供了一种在HTML属性中存储自定义数据的方法

### 伪正则选择器
* [lang|="fr"] :用来选择attr的属性的值是`fr`或者`fr`开头的 用于语言编码处理。
* [data-vegetable*="not spicy"] :用来处理属性值中包含`not spicy`的元素 。
* [data-quantity$="kg"] :用来处理`kg`结尾的元素。
* [data-quantity^="optional"] :用来处理`optional`开头的元素


### 伪类
以`:`作为前缀，被添加到选择器末尾的关键字，当你的元素在特定状态下才本指定的元素。

```html
<a href="https://developer.mozilla.org/" target="_blank">Mozilla Developer Network</a>
```

```css
/* 这些样式将在任何情况下应用于我们
的链接 */

a {
  color: blue;
  font-weight: bold;
}

/* 我们想让被访问过的链接和未被访问
的链接看起来一样 */

a:visited {
  color: blue;
}

/* 当光标悬停于链接，键盘激活或锁定
链接时，我们让链接呈现高亮 */

a:hover,
a:active,
a:focus {
  color: darkred;
  text-decoration: none;
}
```

### 伪元素

使用的是两个冒号`(::)`,添加到选择器后面去选择某个元素的某个部分

domo:

```html
<ul>
  <li><a href="https://developer.mozilla.org/en-US/docs/Glossary/CSS">CSS</a> defined in the MDN glossary.</li>
  <li><a href="https://developer.mozilla.org/en-US/docs/Glossary/HTML">HTML</a> defined in the MDN glossary.</li>
</ul>
```

```css
[href^=http]::after {
  content: '⤴';
}
```

### 组合器和选择器组

| Combinators | 	Select 
| ------ | ------ | ------ |
| A,B | 匹配满足A（和/或）B的任意元素 
| A B | 匹配任意元素，满足条件：B是A的后代结点（B是A的子节点，或者A的子节点的子节点）
|A > B| 匹配任意元素，满足条件：B是A的直接子节点
|A + B| 匹配任意元素，满足条件：B是A的下一个兄弟节点（AB有相同的父结点，并且B紧跟在A的后面）
|A ~ B| 匹配任意元素，满足条件：B是A之后的兄弟节点中的任意一个（AB有相同的父节点，B在A之后，但不一定是紧挨着A）

NOTE:
`+`的意思是当你选择在`+`之前的元素的兄弟元素

```css
h1+p {
  font-style: bold;
  color: blue;
}
```


```html
<h1>Welcome to my website</h1>

<p>Hello, and welcome! I hope you enjoy your time here.</p>
```





# JS

```javascript
var myVariable;
```
javascript 对大小写比较敏感
### 数据类型 
javascript 中任何东西都是对象 
而且对象被存储在变量里面 NB
 
### 运算符
需要注意的是javascript中 两个字符串可以通过`+`连接

### 函数 

```javascript
function multiply(num1,num2){
    var result =num1*num2;
    return result;
}
multiply(4,7)

multiply(4,7)
multiply(4,7)
multiply(4,7)
```

### 事件
```javascript
document.querySelector('html').onclick = function(){
    alert('fucking comming')
}
```
我们选择了`html`这个元素 然后用`onclick`设置成我们想要运行的代码的匿名函数

### example 点击交换图片
```javascript
var myImage = document.querySelector('img')
myImage.onclick = function(){
    var mySrc = myImage.getAttribute('src')
    if (mySrc == 'images/firefox-icon.png'){
        myImage.setAttribute('src','images/firefox2.png')
    }
    else myImage.setAttribute('src','images/firefox-icon.png')
}
var myButton  = document.querySelector('button')
var myHeading = document.querySelector('h1')
``` 
主要是用了`js`中的`setAttribute` 和`getAttribute` 在浅层感觉和`python`的差不多
```html
<html>
        <body>
            <h1>dd</h1>
            <img src="images/firefox-icon.png">
            
            <button>
                Change user
            </button>
            <script src="my.js"></script>
            </body>
</html>
```

### example 使用localStorage
```javascript 
var myButton  = document.querySelector('button')
var myHeading = document.querySelector('h1')
if(localStorage.getItem('name')=='null'){
    setUserName();
}else{
    var storedName = localStorage.getItem('name')
    myHeading.textContent = 'Mozilla is cool' +storedName;
}
function setUserName() {
    var myName = prompt('Please enter your name.');
    localStorage.setItem('name', myName);
    myHeading.textContent = 'Mozilla is cool, ' + myName;
  }

myButton.onclick = function() {
    setUserName();
  }
  ```
  这个东西感觉和后端的session一样 也是存储东西用的 
  但是也不一样 这个骚东西是可以在浏览器关闭后继续存在的
  woc 真的骚


  
