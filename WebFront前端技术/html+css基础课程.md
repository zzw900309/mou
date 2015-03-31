# HTML+CSS基础课程

第1章 Html介绍
--

**1. Html和CSS的关系**

- Html是网页应用的载体，包括文字，图片，视频等
- CSS是样式的表示，用来改变内容的外观
- JavaScript用来实现网页上的特殊效果，动画和交互一般都是由JavaScript实现的

**2. 认识Html标签**

网页是由Html标签组成的

- 网页内容的标题的标签是 `<h1></h1>`
- 网页中文章段落的标签是 `<p></p>`
- 网页中图片的标签是 `<img></img>`

**3. 标签的语法**

- 标签由英文尖括号 `<` 和 `>` 括起来
- Html中标签都是成对出现的，分开始标签和结束标签，结束标签比开始标签多了一个 `/`
- 标签和标签之间是可以嵌套的，但是先后顺序必须保持一致
- Html标签不区分大小写，但是建议都使用小写

**4. 认识Html文件基本结构**

一个Html文件有自己固定的结构

```
<html>
    <head>...</head>
    <body>...</body>
</html>
```

- `<html></html>` 称为根标签，所有的网页标签都在其中
- `<head>` 定义文档头部，是所有头部元素的容器
    - 头部元素有 `<title> <script> <style> <link> <meta>` 等标签
- `<body>` 标签之间是网页的主要内容，会在浏览器中显示出来
    - `<body>` 中有 `<h1><p><a><img>` 等标签

**5. 认识Head标签**

`<head>` 描述了各种网页的属性信息，包括网页标题等，其中绝大部分数据不会显示出来

常见的用在 `<head>` 内的标签：

```
<head>
    <title>...</title>
    <meta>
    <link>
    <style>...</style>
    <script>...</script>
</head>
```
`tilte` 标签内是网页的标题信息，会显示在浏览器的标题栏中

**6. 了解Html的代码注释**

Html代码注释语法：`<!-- 注释内容 -->`

---

第2章 认识标签（第一部分）
--

**1. 语义化**

语义化，是让网页更好的被搜索引擎理解。

语义化的好处

- 更容易被搜索引擎收录
- 更容易让屏幕阅读器读出网页的内容

**2. `<body>` 标签，网页上显示的内容在这里**

在网页上要显示的内容一定要都放在 `<body></body>` 之间

**3. `<p>` 标签，添加段落**

语法：`<p>段落内容</p>`

一段文字是一个 `<p>` 标签，如果一段文章分为3段，就需要放在3个 `<p>` 标签中

`<p>` 标签默认的样式中，段前段后都会有空行，这个空行可以用css样式来删除或改变

**4. `<hx>` 标签，为网页添加标题**

`<hx>` 用来表示文章的标题，一共有6个，h1到h6分别对应一级标题到六级标题，重要性一次递减

语法：`<hx>标题内容</hx>` ，其中x为1到6

标题样式都会加粗，h1字号最大，h6字号最小

**5. 强调语气，使用 `<strong>` 和 `<em>` 标签**

这两个标签都用来表示强调，其中 `<em>` 表示斜体，`<strong>` 表示粗体

语法：

```
<em>需要斜体的文本</em>
<strong>需要加粗的文本</strong>
```

如果不喜欢默认的样式，可以用css改变它

**6. 是用 `<span>` 标签为文字设置单独的样式**

`<span>` 标签没有语义，它的作用是为了设置单独的样式

语法：`<span>文本</span>`

`<span>` 标签内文本的格式可以在 `<head>` 中的 `<style>` 标签中设置：


```
  <style>
      span{
          color:blue;
      }
  </style>
```

**7. `<q>` 标签，短文本引用**

`<q>` 标签表面上是问文本加上双引号，实际上它的语义是：引用内容

语法：`<q>引用内容</q>`

**8. `<blockquote>` 标签，长文本引用**

`<blockquote>` 和 `<q>` 标签一样都表示引用，但是 `<blockquote>` 表示长引用，展现上是整段缩进的样式

语法：`<blockquote>引用文本</blockquote>`

**9. 使用 `<br/>` 标签分行显示文本**

`<br/>` 标签用来对文本进行换行操作

`<br/>` 是一个空标签，空标签只需要写一个开始标签，空标签有 `<br/> <hr/> <img/>`

Html代码中的回车和空格是显示不出来的，想显示回车只能使用 `<br/>`

语法：xhtml1.0：`<br/>`；html4.01：`<br>`

**10. 在网页中增加一些空格**

要在网页中加空格，需要使用 `&nbsp;`，要加几个空格就用几个

**11. `<hr>` 标签，添加水平横线**

语法：html4.01：`<hr>` ；xhtml1.0：`<hr/>`

- `<hr/>` 也是一个空标签，只有开始标签
- `<hr/>` 默认的样式比较粗，是灰色的，可以通过修改css对其进行修改

**12. `<address>` 标签，为网页加入地址信息**

网页中的地址信息要放到 `<address>` 标签中，默认显示的样式是斜体，可以通过修改css来修改

语法：`<address>地址内容</address>`

**13. 用 `<code>` 标签，加入一行代码**

语法：`<code>代码行</code>`

- 如果是多行代码，要使用 `<pre>` 标签

**14. 使用 `<pre>` 标签加入大段代码**

`<pre>` 标签实际上不单是显示源码用的，它的作用是预格式化文本，也就是保留代码中原来的空格和回车等，大部分时候用来表示代码块

使用了 `<pre>` 标签后就不必要再使用 `<br/> &nbsp;` 等

语法：`<pre>代码块</pre>`

---

第3章 认识标签（第二部分）
---

**1. 使用 `<ul>`，添加新闻信息列表**

使用 `<ul> <li>` 标签可以添加没有顺序的新闻列表

语法：

```
	<ul>
    	<li>信息</li>
    	<li>信息</li>
    	...
	</ul>
```

`<ul> <li>` 的默认样式是每一项之前带一个黑色的小圆点

**2. `<ol>` 标签添加有顺序的列表**

`<ol> <li>` 标签可以在网页中添加有顺序的列表

语法：

```
  <ol>
    <li>信息</li>
    <li>信息</li>
    ...
  </ol>
```

`<ol> <li>` 的默认样式是每一项前面带有序号，序号从1开始

**3. `<div>` 在排版中的作用**

网页中，可以把一些独立的逻辑部分划出来，放在一个 `<div>` 标签中，`<div>` 标签相当于一个容器

语法：`<div>...</div>`

**4. 给 `<div>` 命名，使逻辑更加清晰**

可以使用 `id` 属性为 `<div>` 提供唯一的名称，这个id的标识必须是唯一的

语法：`<div id="板块名称">...</div>`

**5. `<table>` 标签，网页上的表格**

要在网页上展示表格需要用到 `<table> <tbody> <tr> <th> <td>` 四个标签

语法：

```
  <table>
    <tr>
        <th>标题1</th>
        <th>标题2</th>
        ...
    </tr>
    <tr>
        <td>内容1</td>
        <td>内容2</td>
        ...
    </tr>
    ...
  </table>
```

- `<table>` 整个表格以 `<table>` 标签开始，以 `</table>` 标签结束
- `<tbody>` 表给内容非常多时候，会边下载边展示，如果加上 `<tbody>` 标签时候，会等所有内容都下载完成后再展示
- `<tr>` 表示表格的一行，有几对 `<tr>` 就表示表格有几行
- `<td>` 单元格，一行中有几对 `<td>` 就表示有几列
- `<th>` 是一种特殊的单元格，用在表头部分

在没有给表格添加css样式之前，表格默认是没有表格线的，表头（`<th>` 标签内部分）文本会默认粗体同时居中显示

**6. 用css样式，为表格加上边框**

在 `<head>` 中用css为表格加上边框：

```
  <style type = "text/css">
    table tr td,th{border:1px solid #000;}
  </style>
```

上面代码的含义是给 `<th> <td>` 单元格加上一个1px的黑色边框

**7. `<caption>` 标签，为表格添加标题和摘要**

摘要不会在浏览器中显示出来，它的作用是增加表格的可读性

语法：`<table summary="表格摘要">`

标题用来描述表格内容，显示在表格上方

语法：

```
  <table>
    <caption>标题文本</caption>
    <tr>
        <td>...</td>
        <td>...</td>
        ...
    </tr>
    ...
  </table>
```

---

第4章 认识标签（第三部分）
--

**1. 使用 `<a>` 标签，链接到别的页面**

`<a>` 标签用来实现超链接

语法：`<a href="目标url" title="鼠标hover文案">链接显示文案</a>`

title的作用主要是方便搜索引擎了解链接地址的内容（语义化）

默认的链接样式是蓝色文字，点击后变为紫色，可以通过css来修改

**2. 在新建浏览器窗口打开链接**

`<a>` 标签默认是在当前窗口打开链接的，要在新的窗口打开，需要加入target

语法：`<a href="目标url" target="_blank">click!</a>`

**3. 使用 `<mailto>` 在网页中链接Email地址**

`<a>` 标签使用 mailto 可以实现发送电子邮件的功能，mailto可以带多个参数：

- 邮箱地址 mailto: `<a href="mailto:ab@abc.com">发送</a>`
- 抄送地址 cc= `<a href="mailto:ab@abc.com?cc=abc@abc.com">发送</a>`
- 密送地址 bcc= `<a href="mailto:ab@abc.com?bcc=abc@abc.com">发送</a>`
- 多个收件人，抄送人，密送人用分号 `<a href="mailto:ab@abc.com;abc@abc.com">发送</a>`
- 邮件主题 subject= `<a href="mailto:ab@abc.com?subject=发送电子邮件">发送</a>`
- 邮件内容 body= `<a href="mailto:ab@abc.com?body=发送电子邮件">发送</a>`

注意，如果mailto后面有多个参数的话，第一个参数用 `?` 开头，后面的参数用 `&` 分隔，如 `<a href="mailto:abc@abc.com?cc=abcd@abc.com&bcc=abcde@abc.com&subject=邮件主题&body=邮件正文">发送</a>`

**4. `<img>` 标签，为网页加入图片**

语法：`<img src="图片地址" alt="下载失败时的替换文本" title="提示文本"/>`

title是指鼠标滑过时显示的文本，alt是图像不可见时的替代文本

图像可以是gif，png，jpeg等格式的文件

---

第5章 与浏览器交互，表单标签
--

**1. 使用表单标签，与用户交互**

网站使用html的表单（form）与用户交互

语法：`<form method="传送方式" action="服务器文件">`

- `<form>` 标签是成对出现的，以 `</form>` 结束
- action 表示用户输入数据被传送到的地方
- method是传送方式（get/post）

范例代码：

```
<from method="post" action="save.php">
    <label for="username">用户名：</label>
    <input type="text" name="username"/>
    <label for="pass">密码：</label>
    <input type="password" name="pass"/>
</form>
```

所有表单控件都需要放在 `<form> </form>` 标签之间

`method:post/get` 的区别 [请查看wiki](http://www.imooc.com/wiki/view?pid=142) ，总而言之，推荐使用 post 方法

**2. 文本输入框，密码输入框**

文本输入框转化为密码输入框

语法：

```
<form>
  <input type="text/password" name="名称" value="文本" />
</form>
```

`type="text"` 时，是文本输入框，`type="password"` 时，是密码输入框

name为文本框命名，给后台ASP、PHP等使用，value是文本框默认的展示值

**3. 文本域，支持多行文本输入**

在表单中输入大段文字，需要用到文本输入域

语法：`<textarea rows="行数" cols="列数">默认文本</textarea>`

cols和rows是输入域的行数和列数，用来决定输入域初始展示时候的大小

cols和rows可以用css样式的width和height来代替

**4. 使用单选框，复选框，让用户选择**

语法：

`<input type="radio/checkbox" value="值" name="名称" checked="checked" />`

`type="radio"` 时，是单选框，`type="checkbox"` 时，是复选框

当设置 `checked="checked"` 时候，该项默认被选中

注意，同一组单选按钮，name样一样，才能起到单选的作用

**5. 使用下拉列表框，节省空间**

下拉列表既可以单选，又可以多选

举例：

```
<form name="iForm">
  <label>爱好：</label>
  <select>
    <option value='读书'>读书</option>
    <option value='运动'>运动</option>
    <option value='音乐'>音乐</option>
    <option value='旅游'>旅游</option>
    <option value='购物' selected="selected">购物</option>
  </select>
</form>
```

说明：`<option value='提交值（向服务器提交）'>选项（显示给用户看）</option>`

`selected="selected"` 表示这一项默认被选中

**6. 使用下拉列表框进行多选**

在select标签中设置 `multiple="multiple"` 属性，可以实现多选功能，使用ctrl或command键进行多选

举例：

```
<form name="iForm">
  <label>爱好：</label>
  <select multiple="multiple">
    <option value='读书'>读书</option>
    <option value='运动'>运动</option>
    <option value='音乐'>音乐</option>
    <option value='旅游'>旅游</option>
    <option value='购物' selected="selected">购物</option>
  </select>
</form>
```

**7. 使用提交按钮，提交数据**

表单中的按钮有两种：提交和重置

提交按钮语法：`<input type="submit" value="提交">`

只有当type的值为submit时候，按钮才有提交的作用

value是按钮上显示的文字

**8. 使用重置按钮，重置表单信息**

语法：`<input tpye="reset" value="重置">`

只有当type的值是reset的时候，按钮才有重置作用

**9. form表单中的label标签**

label的作用是为鼠标用户改进可用性

在label标签内点击文本，会触发控件，当单击选中label标签时，浏览器会自动将焦点转到和标签相关的表单控件上

语法：`<label for="控件id名称">`

注意：标签的for属性中的值应当和相关控件的id属性值一样

举例：

```
<form>
  <label for="male">男</label>
  <input type="radio" name="sex" id="male" />
  <br />
  <label for="female">女</label>
  <input type="radio" name="sex" id="female" />
  <label for="email">输入你的邮箱地址</label>
  <input type="email" id="email" placeholder="Enter email">
</form>
```

---

第6章 开始学习CSS，为网页添加样式
--

**1. 认识CSS样式**

CSS全称为“层叠样式表”，用于定义HTML内容在浏览器内的显示样式，如：

```
p{
  font-size: 12px;
  color: red;
  font-weight: bold;
}
```

**2. CSS样式的优势**

用 `<span>` 标签统一设置样式

**3. CSS代码的语法**

CSS样式由选择符和声明组成，声明由属性和值组成：`p { color: blue }`

选择符又称选择器，指定网页中要应用样式规则的元素

在大括号内的内容是声明。属性和值之间用冒号分隔，有多条声明时，用分号分隔

- 最后一条声明可以没有分号，但为了修改方便，一般也加上分号
- 为了更加方便阅读，一般将每一个声明独立一行

**4. CSS注释代码**

CSS中使用 `/*注释语句*/` 来进行注释

---

第7章 CSS样式基本知识
--

**1. 内联式CSS样式，直接写在现有的HTML标签中**

从CSS代码的插入形式来看分为以下三种：内联式，嵌入式，外部式三种

内联式代码：`<p style="color:red">这里文字是红色</p>`

注意：一定要写在元素的开始标签里面

css样式代码要写在 `style=" "` 中，属性和值用冒号隔开，多条样式中间用分号隔开

**2. 嵌入式CSS样式，写在当前的文件中**

嵌入式CSS样式是把CSS样式代码写在 `<style type="text/css"></style>` 标签之间

一般情况在，嵌入式CSS代码写在 `<head></head>` 之间。如：

```
 <style type="text/css">
   span{
     colr:red;
   }
 </style>
```

**3. 外部式CSS样式，写在单独的一个文件中**

外部式CSS样式把CSS代码写在一个单独的外部文件中，以.css为扩展名，在<head>中使用<link>标签将CSS样式文件链接到HTML文件内，如：

`<link href="base.css" rel="stylesheet" type="text/css" />`

其中，css文件名用有意义的英文命名，`rel="stylesheet" type="text/css"` 是固定的，不能更改

<link> 标签一般在 <head> 标签内

**4. 三种方法的优先级**

三种样式的优先级是：内联式 > 嵌入式/外部式

嵌入式和外部式，谁写在后面（离被设置的元素越近），谁的优先级就最高

- CSS的优先级总体来说就是就近原则
- 上面的优先级有一个前提，就是三个CSS延时是在相同权值的情况下

---

第8章 CSS选择器
--

**1. 什么是选择器**

CSS样式声明中 {} 之前的就是选择器，指明了 {} 中的样式作用的对象

**2. 标签选择器**

标签选择器就是html代码中的标签。如：`<html> <body> <h1> <p> <img>`

**3. 类选择器**

类选择器是CSS样式中最常用到的，语法：`.类选器名称{css样式代码;}`

注意点：英文圆点开头，类选器名称可以起任意英文名

使用方法：

- 用合适的标签把要修饰的内容标记起来：`<span>内容</span>`
- 使用 class="类选择器名称" 为标签设置一个类：`<span class="stress">内容</span>`
- 设置类选器css样式：`.stress{color:red;} /*类前面要加一个英文圆点*/`

**4. ID选择器**

ID选择器很多时候和类选择符类似，但也有些区别：

- 标签设置为 `id="ID名称"`
- ID选择器前面是#，而不是.

**5. 类和ID选择器的区别**

两者的不同点有：

- ID选择器在同一个HTML中只能使用一次，类选择器可是使用多次
- 可以使用类选择器词列表的方式为一个元素同时设置多个样式，ID选择器不可以

```
.stress{
  color:red;
}
.bigsize{
  font-size:25px;
}
 <p>text<span class="stress bigsize">内容</span>text</p>
```

**6. 子选择器**

子选择器用大于符号（>），用于选择指定标签元素的第一代子元素，如：

`.food>li{border:1px solid red;}`

用法如：

```
.first>span{
  border:1px solid red;
}
 <p class="first">text<span>加红框的内容</span>text</p>
```

**7. 包含（后代）选择器**

包含选择器使用空格，用于选择指定标签元素下的后辈元素

与子选择器的区别：

- 子选择器仅指它的直接后代，即第一代后代
- 后代选择器是作用于所有的子后代元素，即无论多层嵌套，都会使用该样式

**8. 通用选择器**

通用选择器是功能最强大的选择器，用星号（*）指定，匹配HTML中的所有标签，如：

`* {color:red;}`

**9. 伪类选择符**

伪类选择符给html不存在的标签设置样式，如鼠标划过的状态hover

`a:hover{color:red;}`

- 目前只有hover是在左右浏览器上都兼容的伪类选择符
- :hover可以放在任意标签上，但是除了a之外，其他的兼容性也不是很好

**10. 分组选择符**

给HTML中多个标签设置同一个样式的时候，可以使用分组选择符（,）：

`h1,span {color:red;}`

---

第9章 CSS样式的继承，层叠和特殊性
--

**1. 继承**

继承是一种规则，使样式不仅应用于特定的html标签，也用于他们的后代

有些CSS样式不具有继承性，如：`border:1px solid red;`

**2. 特殊性**

浏览器根据CSS权值的高低来判断使用哪一种CSS样式，权值规则：

标签的权值是1，类选择符的权值是10，ID选择符权值最高，是100，如：

```
p{color:red;}  /*权值是1*/
p span{color:green;}  /*权值是1+1=2*/
.warning{color:white;}  /*权值是10*/
p span.warning{color:purple;}  /*权值是1+1+10=12*/
#footer .note p{color:yellow;}  /*权值是100+10+1=111*/
```

继承也有权值，但是很低

**3. 层叠**

对于同一个元素，有多个CSS样式存在且有同样的权重，就需要靠层叠来判断

层叠判断的标准：处于最后面的CSS样式会被应用

所以前面提到的：内联样式表>嵌入样式表>外部样式表

**4. 重要性**

特殊情况下，需要为某些样式设置具有最高权值，这时使用 !important 来解决，如：

```
p{color:red!important;}
p{color:green;}
 <p class="first">text</p>
```

注意，!important 要写在分号前面

样式在浏览器中的优先级为：浏览器默认的样式<网页制作者样式<用户自己设置的样式，但是!important样式是一个例外

---

第10章 CSS格式化排版
--


**1. 文字排版-字体**

设置字体举例：`body{body-family:"宋体";}`

不要使用不常用的字体，现在的网页喜欢使用微软雅黑：

```
body{font-family:"Microsoft Yahei";}  /*兼容性较好*/
body{font-family:"微软雅黑";}
```

**2. 文字排版-字号，颜色**

举例：`body{font-size:12px; color:#666;}`

**3. 文字排版-粗体**

举例：`p span{font-weight:bold;}`

**4. 文字排版-斜体**

举例：`p a{font-style:italic;}`

**5. 文字排版-下划线**

举例：`p a{text-decoration:underline;}`

**6. 文字排版-删除线**

举例：`.oldPrice{text-decoration:line-through;}`

**7. 段落排版-缩进**

在段前加入两个文字的空白：`p{text-indent:2em;}`

其中，2em指文字的两倍大小

**8. 段落排版-行间距（行高）**

举例：`p{line-height:1.5em;}`

**9. 段落排版-字间距，字母间距**

设置字母间距：`h1{letter-spacing:50px;}`

设置单词之间的间距：`h1{word-spacing:50px;}`

**10. 段落排版-对齐**

为块状元素中的文本，图片设置对齐样式：

```
h1{text-align:center;}  /*居中对齐*/
h1{text-align:left;}  /*左对齐*/
h1{text-align:right;}  /*右对齐*/
```

---

第11章 CSS盒模型
--

**1. 元素分类**

在CSS中，html的标签大体被分为三类：块状元素，内联元素（行内元素）和内联块状元素

常见块状元素：

```
 <div> <p> <h1>...<h6> <ol> <ul> <dl> <table> <address> <blockquote> <form>
```

常见的内联元素：

```
 <a> <span> <br> <i> <em> <strong> <label> <q> <var> <cite> <code>
```

常见的内联块状元素：

```
 <img> <input>
```

**2. 元素分类-块级元素**

通过 `display:block` 将其他元素显示为块级元素，使其有块级元素的特点，如：`a{display:block;}`

块级元素的特点：

- 每个块级元素都从新一行开始
- 元素的高度，宽度，行高，顶和底边距都可以设置
- 元素宽度不设置的情况下，默认是父容器的100%

**3. 元素分类-内联元素**

通过 `display:inline` 将元素设置为内联元素

内联元素特点：

- 和其他元素都在一行上
- 元素的高度，宽度，行高，顶部和底部边距不可设置
- 元素的宽度就是它包含的文字或图片的高度，不可改变

**4. 元素分类-内联块状元素**

内联块状元素同时具有内联元素和块状元素的特点

`display:inline-block` 将元素设置为内联块状元素

内联块状元素特点：

- 和其他元素都在一行上
- 元素的高度，宽度，行高，顶和底边距都可以设置

**5. 什么是盒模型**

盒子模型：

- 盒子模型的外框和内部元素间的距离：内填充，padding
- 盒子模型之间的距离：外边距，margin
- 盒子模型的边框：border

padding，margin和border都有四个方向；块级元素标签都有盒子模型的特征

**6. 盒模型-边框（一）**

边框有粗细，样式，颜色三个属性：`div{border:2px solid red;}`

上面的是缩写形式，可以分开写：

```
div{
  border-weight:2px;
  border-style:solid;
  border-color:red;
}
```

- border-style的常见样式有：dashed（虚线），dotted（点线），solid（实线）
- border-color可以用十六进制颜色
- border-width也可以设置为thin，medium，thick，但是不常用，一般用像素

**7. 盒模型-边框（二）**

CSS中允许只给一个方向的边框设置样式：`div{border-bottom:1px solid red;}`

**8. 盒模型-宽度和高度**

CSS内定义的宽和高，是指填充以里的内容范围，一个元素的实际宽度：左边界+左边框+左填充+内容宽度+右填充+右边框+右边界

举例：

```
div{
  width:200px;
  padding:20px;
  border:1px solid red;
  margin:10px;
}
```

chrome可以直接查看盒模型

**9. 盒模型-填充**

填充指元素内容与边框之间的距离，填充分为上，右，下，左（顺时针），如：`div{padding:20px 10px 15px 30px;}`

注意顺序不要混淆，上面的代码分开来写就是：

```
div{
  padding-top:20px;
  padding-right:10px;
  padding-bottom:15px;
  padding-left:30px;
}
```

如果4个方向填充一样，可以缩写：`div{padding:10px;}`

如果上下都是10px，左右都是20px，可以缩写：`div{padding:10px 20px;}`

**10. 盒模型-边界**

边界指元素和其他元素间的距离，方向也是上，右，下，左：`div{margin:20px 10px 15px 30px;}`

也可以分开写：

```
div{
  margin-top:20px;
  margin-right:10px;
  margin-bottom:15px;
  margin-left:30px;
}
```

四边边界一样时，可以缩写：`div{margin:10px;}`

如果上下边界是10px，左右都是20px，可以缩写：`div{margin:10px 20px;}`

---

第12章 CSS布局模型
--

**1. CSS布局模型**

CSS包含三种基本的布局模型：

- 流动模型 FLow
- 浮动模型 Float
- 层模型 Layer

**2. 流动模型（一）**

流动模型是默认的网页布局样式，有两个比较典型的特征：

- 块状元素都会在所处的包含元素内自上而下按顺序垂直衍生分布

**3. 流动模型（二）**

第二个特征，内联元素都会在所处的包含元素内从左到右水平分布显示

**4. 浮动模型**

使用CSS可以将元素定义为浮动，使块状元素在同一行显示：

```
div{
  weight:200px;
  height:200px;
  border:2px red solid;
  float:left;  /*定义为浮动*/
}
```

也可以设置为右浮动:`float:right;`

**5. 什么是层模型**

CSS定义了一组定位属性来支持层布局模型，层模型有三种形式：

- 绝对定位（position:absolute）
- 相对定位（position:relative）
- 固定定位（position:fixed）

**6. 层模型-绝对定位**

使用 `position:absolute` 将元素从文档流中拖出来，然后使用 `left right top bottom` 相对于其最接近的一个具有定位属性的父包含块进行绝对定位

如果不存在这样的包含块，就相对于body元素，即浏览器窗口

```
div{
  width:200px;
  height:200px;
  border:2px red solid;
  position:absolute;  /*绝对定位*/
  left:100px;  /*距左边框100px*/
  top:50px;  /*距右边框50px*/
}
```

**7. 层模型-相对定位**

通过 `position:relative` 来设置相对定位，相对定位完成过程：

- 按static(float)方式生成一个元素
- 相对于以前的位置移动，移动的方向和幅度由 `left right top bottom` 属性决定
- 偏移前的位置保留不动

```
div{
  width:200px;
  height:200px;
  border:2px red solid;
  position:relative;  /*相对定位*/
  left:100px;  /*距左边框100px*/
  top:50px;  /*距右边框50px*/
}
```

**8. 层模型-固定定位**

fixed表示固定定位，它相对移动的坐标是视图本身，不会随浏览器窗口的滚动条变化而变化

```
div{
  width:200px;
  height:200px;
  border:2px red solid;
  position:fixed;
  left:100px;
  top:50px;
}
```

**9. Relative与Absolute组合使用**

绝对定位的元素可以相对于其他元素来定位，注意：

- 参照定位的元素必须是相对定位元素的前辈元素
- 参照定位元素必须加入 `position:relative;`
- 定位元素加入 `position:absolute;`，就可以使用 top bottom left right 来进行偏移定位了

---

第13章 CSS代码缩写，占用更少的带宽
--

**1. 盒模型代码简写**

margin，padding，border设置是按照顺时针方向（上右下左）设置的，通常有3种缩写方法：

- 四个方向值相同：
  
  ```
  margin:10px 10px 10px 10px
  margin:10px;  /*缩写*/
  ```
- top和bottom相同，left和right相同：
  
  ```
  margin:10px 20px 10px 20px;
  margin:10px 20px;  /*缩写*/
  ```
- 如果left和right的值相同
  
  ```
  margin:10px 20px 30px 20px;
  margin:10px 20px 30px;  /*缩写*/
  ```

padding，border的缩写和margin是一样的

**2. 颜色值缩写**

当设置的颜色的16进制色彩值每两位相同时候，可以缩写一半：

```
color:#336699;
color:#369;  /*缩写*/
```

**3. 字体缩写**

字体的CSS样式代码也有自己的缩写方式，如：

```
body{
  font-style:italic;
  font-variant:small-caps;
  font-weight:bold;
  font-size:12px;
  line-height:1.5em;
  font-family:"宋体",sans-serif;
}
```

可以缩写为：

```
body{
  font:italic small-caps bold 12px/1.5em "宋体",sans-serif;
}
```

- 简写时候至少指定 font-size 和 font-family，其他属性没有指定时候将使用默认值
- 缩写时候，font-size 和 line_height 之间要加入斜杠（“/”）

一般的中文网站，下面代码比较实用：

```
body{
  font:12px/1.5em "宋体",sans-serif;
}
```

---

第14章 单位和值
--

**1. 颜色值**

设置颜色的方法有很多种：

英文命令颜色：`p{color:red;}`

RGB颜色：`p{color:rgb(133,45,200);}`

- 每一项是0-255之间的整数，也可以是0%-100%的百分数：`p{color:rgb(20%,33%,25%);}`

十六进制颜色，这个是现在普遍使用的方法：`p{color:#00ffff;}`

**2. 长度值**

比较常用的长度单位有 px（像素），em，%（百分比），这三个单位都是相对单位

- 像素：CSS规范中假设90像素为1英寸，目前大多数设计倾向于像素做单位
- em：指本元素给定字体的font-size值，如果font-size为14px，则1em=14px
  - 当font-size的单位是em时，此时计算的标准以父元素的font-size为基础，如：
  
    ```
    p{font-size:14px;}
    span{font-size:0.8em;}  /*span是p的子元素，span的字体大小为14*0.8=11.2px*/
    ```
- 百分比：设置行间距是字体的百分比 `p{font-size:12px;line-height:130%;}`

---