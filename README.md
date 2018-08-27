# front-end-review
前端复习
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


  
