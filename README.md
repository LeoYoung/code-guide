# HTML与CSS代码规范
为开发灵活、健壮、连贯的HTML以及CSS而制定的标准



----------



## 内容目录

* [黄金准则](#黄金准则)
* [HTML](#html)
  * [HTML规则](#HTML规则)
  * [HTML5文档类型](#HTML5文档类型)
  * [实用语义](#实用语义)
  * [属性顺序](#属性顺序)
  * [JavaScript生成标签](#JavaScript生成标签)
* [CSS](#css)
  * [CSS规则](#CSS规则)
  * [声明顺序](#声明顺序)
  * [例外格式](#例外格式)
    * [前置属性](#前置属性)
    * [单条声明规则](#单条声明规则)
  * [友好可读性](#友好可读性)
    * [注释](#注释)
    * [Class名](#Class名)
    * [选择器](#选择器)
  * [组织](#组织)
* [Writing copy](#copy)
  * [Sentence case](#sentence-case)



----------



## 黄金准则

> 代码库中的所有代码无论是多少人共同贡献的成果，都应该看起来是一个人写的。

这就意味着要时刻严格的执行规约中的条款。添加或者修正，请[在Github上作为一个议题](https://github.com/markdotto/code-guide)。



----------



## HTML


### HTML句法

* 使用两个空格作为缩进
* 子元素应该缩进一次（两空格）
* 只使用双引号，不要使用单引号
* 在闭合元素后不要使用斜杠

**反例:**

````html
<!DOCTYPE html>
<html>
<head>
<title>Page title</title>
</head>
<body>
<img src='images/company-logo.png' alt='Company' />
<h1 class='hello-world'>Hello, world!</h1>
</body>
</html>
````

**正例:**

````html
<!DOCTYPE html>
<html>
  <head>
    <title>Page title</title>
  </head>
  <body>
    <img src="images/company-logo.png" alt="Company">
    <h1 class="hello-world">Hello, world!</h1>
  </body>
</html>
````


### HTML5文档类型

在每个HTML页面头部使用基本文件类型以强制使用浏览器的标准模式

````html
<!DOCTYPE html>
````


### 实用语义

尽量让HTML标准并且符合语义，不过不要牺牲实用性。在任何可能的时候都使用最少的标签以及内容。


### 属性顺序

HTML属性应该以特定的顺序排序以增加代码的可读性。

* class
* id
* data-*
* for|type|href

你的标签应该像这样:

````html
<a class="" id="" data-modal="" href="">Example link</a>
````

### JavaScript生成标签

在JavaScript文件中写标签会让其内容难以检索，难以编辑并且低效。所以不要这么做。



----------



## CSS

### CSS规则

* 使用两个空格作为缩进
* 当组合选择器时，保持每项的选择器在不同行
* 声明段中的左花括号前应该有一个空格
* 声明段中的右花括号应该另起一行
* 任何属性的 <code>:</code> 后都应有个空格
* 每个声明都应该单独分行
* 每个声明都应该以分号结尾
* 逗号分割的值都应该在逗号后有一个空格
* 不要再RGB或者RGBa颜色的逗号后添加空格，不要在值前加0
* 小写所有的hex值，例如, <code>#fff</code> 而不是 <code>#FFF</code>
* 计量使用简写方式，例如, <code>#fff</code> 而非 <code>#ffffff</code>
* 用引号引起选择其中的值，例如, <code>input[type="text"]</code>
* 避免给0值使用指定单位，例如, <code>margin: 0;</code> 而非 <code>margin: 0px;</code>

**反例:**

````css
.selector, .selector-secondary, .selector[type=text] {
  padding:15px;
  margin:0px 0px 15px;
  background-color:rgba(0, 0, 0, 0.5);
  box-shadow:0 1px 2px #CCC,inset 0 1px 0 #FFFFFF
}
````

**正例:**

````css
.selector,
.selector-secondary,
.selector[type="text"] {
  padding: 15px;
  margin: 0 0 15px;
  background-color: rgba(0,0,0,.5);
  box-shadow: 0 1px 2px #ccc, inset 0 1px 0 #fff;
}
````

对这里使用的条款有任何问题？参见维基百科[层叠样式表书写规则](http://en.wikipedia.org/wiki/Cascading_Style_Sheets#Syntax)词条


### 声明顺序

相关的声明应该排列在一起，将位置以及盒模型属性排列在最上边，之后是样式以及显示属性

````css
.declaration-order {
  /* Positioning */
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 100;

  /* Box-model */
  display: block;
  float: right;
  width: 100px;
  height: 100px;

  /* Typography */
  font: normal 13px "Helvetica Neue", sans-serif;
  line-height: 1.5
  color: #333;
  text-align: center;

  /* Visual */
  background-color: #f5f5f5;
  border: 1px solid #e5e5e5;
  border-radius: 3px;

  /* Misc */
  opacity: 1;
}
````

完整的属性顺序，请参见[Recess](http://twitter.github.com/recess)。


### 例外格式

在某些情况下，明显不按照默认的[规则](#CSS规则)也很有必要。

#### 前置属性

当使用一些厂商前置属性时，缩进每个属性以使值竖列垂直从而方便编辑

````css
.selector {
  -webkit-border-radius: 3px;
     -moz-border-radius: 3px;
          border-radius: 3px;
}
````

In Textmate, use **Text &rarr; Edit Each Line in Selection** (&#8963;&#8984;A). In Sublime Text 2, use **Selection &rarr; Add Previous Line** (&#8963;&#8679;&uarr;) and **Selection &rarr;  Add Next Line** (&#8963;&#8679;&darr;).

#### 单条声明规则

在实际中，当多个规则都仅存在一个单个声明的时候，考虑为了易读和便于编辑而不使用换行。

````css
.span1 { width: 60px; }
.span2 { width: 140px; }
.span3 { width: 220px; }

.sprite {
  display: inline-block;
  width: 16px;
  height: 15px;
  background-image: url(../img/sprite.png);
}
.icon           { background-position: 0 0; }
.icon-home      { background-position: 0 -20px; }
.icon-account   { background-position: 0 -40px; }
````


### 友好可读性

代码由人编写跟维护。确保你的代码叙述清楚，有良好的注释以及对别人易于上手

#### 注释

良好的注释可以传递背景或者目的，不要仅仅重申一个元素或者类名

**反例:**

````css
/* Modal header */
.modal-header {
  ...
}
````

**正例:**

````css
/* Wrapping element for .modal-title and .modal-close */
.modal-header {
  ...
}
````

#### Class名

* 保持类名小写并且使用破折号（不要使用下划线和驼峰写法）
* 避免使用随意的简写
* 保持类名尽量短
* 使用有意义的名字，要看上去有结构性跟目的性
* 类名前置需要基于最邻近父元素的类名

**反例:**

````css
.t { ... }
.red { ... }
.header { ... }
````

**正例:**

````css
.tweet { ... }
.important { ... }
.tweet-header { ... }
````

#### 选择器

* 在通用的标签中使用类
* 保持选择器选择元素最多不超过三个
* 必要时通过最近父元素来范围定义类（例如不适用前置类时）

**反例:**

````css
span { ... }
.page-container #stream .stream-item .tweet .tweet-header .username { ... }
.avatar { ... }
````

**正例:**

````css
.avatar { ... }
.tweet-header .username { ... }
.tweet .avatar { ... }
````

### 组织

* 通过组成部分来组织代码
* 制定一个一致的注释层次结构
* 如果使用多个CSS文件，通过组成部分来分割他们



----------



## Copy

### Sentence case

Always write copy, including headings and code comments, in [sentence case](http://en.wikipedia.org/wiki/Letter_case#Usage). In other words, aside from titles and proper nouns, only the first word should be capitalized.



----------



### Thanks

Heavily inspired by [Idiomatic CSS](https://github.com/necolas/idiomatic-css) and the [GitHub Styleguide](http://github.com/styleguide). Made with all the love in the world by [@mdo](http://twitter.com/mdo).
