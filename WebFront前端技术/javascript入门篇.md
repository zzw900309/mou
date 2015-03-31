# JavaScript入门篇

第1章 请做好准备
--

**1. 为什么学习JavaScript**

**2. 新朋友你在哪里（如何插入JS）**

使用`<script>`标签在html里面插入JavaScript代码，把JS代码写在标签里面：`<script type="text/javascript">`

type告诉html插入的是JS

**3. 我也可以独立（引用JS外部文件）**

可以将html和js代码分开，单独创建一个js文件，将js文件嵌入到html文件中：`<script src="script.js"></script>`

**4. 找到你的位置（JS在页面中的位置）**

JS代码一般放在网页的head或body部分

- 放在head部分，浏览器在解析head部分时候会执行代码，之后再解析页面其余部分
- 放在body部分，JS代码在网页读到该语句时候执行

浏览器解释html是按先后顺序的，前面的script先被执行，所以初始化的js必须放在head里面

**5. 认识语句和符号**

每一句JS代码格式：`语句;` 通常在结尾加上分号（“;”）表示语句的结束，举例：

```
 <script type="text/javascript">
  document.write("I");
  document.write("Love");
  document.write("JavaScript");
 </script>
```

JS中的代码和符号都要在英文状态下输入，结尾的分号可以不写，但是要培养良好习惯，加上分号

**6. 注释很重要**

单行注释，在注释内容前加符号 “//”

```
 <script type="text/javascript">
   document.write("内容");  //注释内容
 </script>
```

多行注释，以`/*`开始，以`*/`结束

```
 <script type="text/javascript">
   document.write("内容");
   /*
    多行注释
    多行注释
   */
 </script>
```

**7. 什么是变量**

定义变量使用关键字var：`var 变量名`

变量名可以任意取名，但是要遵循命名规则：

- 变量名必须使用字母或者下划线（_）开始
- 变量名必须由英文字母，数字，下划线组成
- 变量名不能用JS关键词和JS保留字

变量要先声明再赋值：

```
var mychar;
mychar = "javascript";
var mynum = 6;
```

变量可以重复赋值：

```
var mychar;
mychar = "javascript";
mychar = "hello";
```

注意：

- JS区分大小写，mychar和myChar是两个变量
- 变量可以不声明直接使用，但是不规范

**8. 判断语句（if...else）**

语法：

```
if(条件)
{ 条件成立时候执行的代码 }
else
{ 条件不成立时候执行的代码 }
```

**9. 什么是函数**

函数是完成某个特定功能的一组语句。定义函数：

```
function 函数名()
{
  函数代码;
}
```

- function是定义函数的关键字
- 函数名是 为函数取的名字
- 函数代码是完成特定功能的代码

调用函数：在需要的位置写下函数

```
 <script type="text/javascript">
   function contxt() //定义函数
   {
     alert("哈哈，调用函数了!");
   }
 </script>
 <body>
   <form>
      <input type="button"  value="点击我" onclick="contxt()" />  /*直接调用函数*/
   </form>
 </body>
```

---

第2章 请和我互动（常用互动方法）
--

**1. 输出内容**

`document.write()`可以在网页中输出内容

第一种，输出内容用“”括起，直接输出“”内的内容

```
 <script type="text/javascript">
   document.write("I love JS!");  //直接输出“”内的内容
 </script>
```

第二种，通过变量，输出内容：

```
 <script type="text/javascript">
   var mystr="hello world!";
   document.write(mystr);  //输出变量的内容
 </script>
```
第三种，输出多项内容，内容之间用加号（“+”）连接：

```
 <script type="text/javascript">
   var mystr="hello";
   document.write(mystr+"I love JS!");  //多项内容之间用+连接
 </script>
```

第四种，输出html，并起作用，标签使用“”括起来

```
 <script type="text/javascript">
   var mystr="hello";
   document.write(mystr+"<br>");  //输出hello后，输出一个换行符
   document.write("JavaScript");
 </script>
```

**2. 警告（alert消息对话框）**

语法：`alert(字符串或变量);`

alert弹出的消息对话框包含一个确定按钮

- 点击对话框的确定前，不能进行任何其他操作
- 通常用于调试程序
- 输出的内容，可以是字符串或者变量，与document.write相似

**3. 确认（confirm消息对话框）**

confirm消息对话框允许用户做选择操作，包括一个确定按钮和取消按钮，语法：`confirm(str);`

str：在消息对话框中要显示的文本

返回值：

- 返回的是boolean值
- 当用户点击确定时，返回true
- 用户点击取消时，返回false

**4. 提问（prompt消息对话框）**

通常用来询问一些需要与用户交互的信息，包含一个确定按钮，取消按钮和一个文本输入框，语法：`prompt(str1, str2);`

- str1：显示在消息对话框中的文本，不可修改
- str2：显示在文本框中的内容，可以修改

返回值：

- 点击确定，文本框中的内容作为函数的返回值
- 点击取消，返回null

**5. 打开新窗口（window.open）**

语法：`window.open(<URL>,<窗口名称>,<参数字符串>)`

举例：

```
 <script type="text/javascript">
   window.open('http://www.imooc.com','_blank','width=300,height=200,menubar=no,toolbar=no, status=no,scrollbars=yes');
 </script>
```

参数说明：

- URL：打开窗口的网址或路径
- 窗口名称：被打开窗口的名称，可以是“_top”、“_blank”、“_selft”等
- 参数字符串：设置窗口的参数，各参数用逗号隔开

参数表：

| 参数 | 值 | 说明 |
| -- | -- | -- |
| top | Number | 窗口顶部距离屏幕顶部的像素数 |
| left | Number | 窗口左端距离屏幕左边的像素数 |
| width | Number | 窗口的宽度 |
| height | Number | 窗口的高度 |
| menubar | yes/no | 窗口有没有菜单 |
| toolbar | yes/no | 窗口有没有工具条 |
| scrollbars | yes/no | 窗口有没有滚动条 |
| status | yes/no | 窗口有没有状态栏 |

注意：

- 参数之间逗号及等号之间有空格，该字符串无效
- 运行结果需要考虑浏览器兼容性问题

**6. 关闭窗口（window.close）**

用法：

```
window.close();  //关闭本窗口
<窗口对象>.close();  //关闭指定的窗口
```

举例：关闭新建的窗口

```
 <script type="text/javascript">
   var mywin = window.open('http://www.imooc.com');
   mywin.close();
 </script>
```

**7. 编程练习**

制作新按钮，“新窗口打开网站” ，点击打开新窗口。

```
<!DOCTYPE html>
<html>
 <head>
  <title> new document </title>  
  <meta http-equiv="Content-Type" content="text/html; charset=gbk"/>   
  <script type="text/javascript">  
    function openWindow(){
    // 新窗口打开时弹出确认框，是否打开
      var conf = confirm("是否打开网站");
      if (conf == true)
      {
        // 通过输入对话框，确定打开的网址，默认为 http：//www.imooc.com/
        var url = prompt("输入网址：","http://www.imooc.com/");
      }      
    //打开的窗口要求，宽400像素，高500像素，无菜单栏、无工具栏。
      window.open('url','_blank','width=400,height=500,menubar=no,toolbar=no');
    }
  </script> 
 </head> 
 <body> 
	  <input type="button" value="新窗口打开网站" onclick="openWindow()" /> 
 </body>
</html>
```

---

第3章 你也有控制权（DOM操作）
--

**1. 认识DOM**

DOM：文档对象模型。定义访问和处理html文档的标准方法，将html文档呈现为带有元素，属性和文本的树结构

Html文档是由节点构成的集合，常见的DOM节点：

- 元素节点：如html，body，p等都是元素节点
- 文本节点：向用户展示的内容，如`<li>...</li>`中的JS，DOM，CSS等文本
- 属性节点：元素属性，如a标签的链接属性`href="http://www.imooc.com"`

**2. 通过ID获取元素**

网页通过标签将信息组织起来，标签的id属性值是唯一的，可以通过id先找到标签，然后操作，语法：`document.getElementById("id")`

获取的元素是一个对象，要对元素进行操作，还是要通过它的属性或者方法，所以getElementById的结果是 null 或 [object HTMLParagraphElement]

**3. innerHTML属性**

innerHTML用于获取或替换HTML元素的内容，语法：`Object.innerHTML`

注意：

- Object是获取的元素对象，如通过document.getElementById获取的元素
- innerHTML区分大小写

举例：

```
 <p id="con">Hello World!</p>
 <script>
   var mycon = document.getElementById("con");
   document.write("p标签原始内容："+mycon.innerHTML+"<br>");
   mycon.innerHTML = "New text!";
   document.write("p标签修改后内容："+mycon.innerHTML);
 </script>
```

**4. 改变HTML样式**

HTML DOM允许JS改变HTML样式，语法：`Object.style.property = new style;`

以下是常用的一小部分属性，其他样式也可以使用这个方法修改：

| 属性 | 描述 |
| -- | -- |
| backgroundColor | 设置元素的背景颜色 |
| height | 设置元素的高度 |
| width | 设置元素的宽度 |
| color | 设置文本的颜色 |
| font | 在一行设置所有字体属性 |
| fontFamily | 设置元素的字体系列 |
| fontSize | 设置元素的字体大小 |

举例：

```
 <p id="pcon">Hello World!</p>
 <script>
   var mychar = document.getElementById("pcon");
   mychar.style.color="red";
   mychar.style.fontSize="20";
   mychar.style.backgroundColor="blue";
 </script>
```

**5. 显示和隐藏（display属性）**

语法：`Object.style.display = value`

value取值：

- none：此元素不会被显示（隐藏）
- block：此元素将显示为块级元素（显示）

举例：`document.getElementById("con").style.display = "none";`

**6. 控制类名（className属性）**

className属性设置或返回元素的class属性，语法：`object.className = classname`

作用：

- 获取元素的class属性
- 为网页内的某个元素制定一个css样式来更改该元素外观

举例：

```
 <!DOCTYPE HTML>
 <html>
 <head>
 <meta http-equiv="Content-Type" content="text/html; charset=gb2312">
 <title>className属性</title>
 <style>
     body{ font-size:16px;}
     .one{
 		border:1px solid #eee;
 		width:230px;
 		height:50px;
 		background:#ccc;
 		color:red;
     }
 	.two{
 		border:1px solid #ccc;
 		width:230px;
 		height:50px;
 		background:#9CF;
 		color:blue;
 	}
 	</style>
 </head>
 <body>
     <p id="p1" > JavaScript使网页显示动态效果并实现与用户交互功能。</p>
     <input type="button" value="添加样式" onclick="add()"/>
 	<p id="p2" class="one">JavaScript使网页显示动态效果并实现与用户交互功能。</p>
     <input type="button" value="更改外观" onclick="modify()"/> 

 	<script type="text/javascript">
 	   function add(){
 	      var p1 = document.getElementById("p1");
 	      p1.className = "one";
 	   }
 	   function modify(){
 	      var p2 = document.getElementById("p2");
 	      p2.className = "two";
 	   }
 	</script>
 </body>
 </html>
```

---

第4章 编程挑战
--

请编写"改变颜色"、"改变宽高"、"隐藏内容"、"显示内容"、"取消设置"的函数，点击相应按钮执行相应操作，点击"取消设置"按钮后，提示是否取消设置，如是执行操作，否则不做操作。

```
 <!DOCTYPE HTML>
 <html>
 <head>
 <meta http-equiv="Content-Type" Content="text/html; charset=utf-8" />
 <title>javascript</title>
 <style type="text/css">
 body{font-size:12px;}
 #txt{
     height:400px;
     width:600px;
 	border:#333 solid 1px;
 	padding:5px;}
 p{
 	line-height:18px;
 	text-indent:2em;}
 </style>
 </head>
 <body>
   <h2 id="con">JavaScript课程</H2>
   <div id="txt"> 
      <h5>JavaScript为网页添加动态效果并实现与用户交互的功能。</h5>
         <p>1. JavaScript入门篇，让不懂JS的你，快速了解JS。</p>
         <p>2. JavaScript进阶篇，让你掌握JS的基础语法、函数、数组、事件、内置对象、BOM浏览器、DOM操作。</p>
         <p>3. 学完以上两门基础课后，在深入学习JavaScript的变量作用域、事件、对象、运动、cookie、正则表达式、ajax等课程。</p>
   </div>
   <form>
   <!--当点击相应按钮，执行相应操作，为按钮添加相应事件-->
     <input type="button" value="改变颜色" onclick="changeColor()"/>  
     <input type="button" value="改变宽高" onclick="changeSize()"/>
     <input type="button" value="隐藏内容" onclick="setHidden()"/>
     <input type="button" value="显示内容" onclick="setShow()"/>
     <input type="button" value="取消设置" onclick="setDefault()"/>
   </form>
   <script type="text/javascript">
     var mychar = document.getElementById("txt");
     //定义"改变颜色"的函数
       function changeColor(){
         mychar.style.color = "red";
         mychar.style.backgroundColor = "green";
       }
     //定义"改变宽高"的函数
       function changeSize(){
         mychar.style.width = "400px";
         mychar.style.height = "500px";
       }
     //定义"隐藏内容"的函数
       function setHidden(){
         mychar.style.display = "none";  
       }
     //定义"显示内容"的函数
       function setShow(){
         mychar.style.display = "block";  
       }
     //定义"取消设置"的函数
       function setDefault(){
         var conf = confirm("确定取消设置？");
         if (conf==true) {
           mychar.removeAttribute('style');
         }
       }
   </script>
 </body>
 </html>
```