# JavaScript进阶篇

第1章 系好安全带，准备启航
--

**1. 让你认识JS**

JS能做什么：

- 增强网页动态效果（下拉菜单，图片轮播，信息滚动等）
- 实现页面与用户之间的实时、动态交互

课程内容：JS的变量，数组，函数，语法，对象，事件，DOM操作

**2. 编程练习**

---

第2章 你要懂的规则（JS基础语法）
--

**1. 什么是变量**

变量是用来存储某种/某些数值的存储器

**2. 给变量取个名字（变量命名）**

变量名可以任意取，但是有一定的规则：

- 必须以字母，下划线或者美元符号开头，后面可以跟字母，下划线，美元符号和数字
- 变量名区分大小写，
- 不允许使用JS关键字和保留字做变量名

**3. 确定你的存在（变量声明）**

变量声明语法：`var 变量名;`

可以一次声明多个变量，中间用逗号（“,”）隔开：`var num1,num2;`

变量可以不声明就直接使用，但是为了规范，一般都是先声明，后使用

**4. 多样化的我（变量赋值）**

使用等于号（“=”）给变量存储内容，语法：`var mynum = 5;`

也可以拆开来写：

```
var mynum;
mynum = 5;
```

变量可以存储多种格式的数据，数值，字符串，布尔值等

```
var num = 123;
var num2 = "一二三";
var num3 = true;
```

**5. 表达出你的想法（表达式）**

具有一定的值，用操作符把常熟和变量连接起来的代数式，表达式有：

- 串表达式：`"I"+"love"+mychar`，值为字符串
- 数值表达式：`num+2*3`，值为数值
- 布尔表达式：`num == 5`，值为true或false

**6. 我还有其他用途（+号操作符）**

JS中的操作符：

- 算术操作符：+，-，*，/ 等
- 比较操作符：>，<，>=，<= 等
- 逻辑操作符：&&，||，! 等
- 赋值操作符：=

“+”操作符，在JS中，除了代表加法，还可以连接两个字符串

**7. 自加一，自减一（++和--）**

举例：

```
var mynum=10;
mynum++;  //等同于 mynum=mynum+1; mynum的值为11
mynum--;  //等同于 mynum=mynum-1; mynum的值变为10
```

**8. 较量较量（比较操作符）**

两个操作数通过比较操作符进行比较，得到值为真（true）或假（false）

比较操作符：

| 操作符 | 描述 |
| -- | -- |
| < | 小于 |
| > | 大于 |
| <= | 小于等于 |
| >= | 大于等于 |
| == | 等于 |
| != | 不等于 |

**9. 我与你同在（逻辑与操作符）**

语法：`b>a && b<c`，只有当两边都为真时，整个表达式才为真

逻辑与操作符值表：

| A | B | A && B |
| -- | -- | -- |
| true | true | true |
| true | false | false |
| false | true | false |
| false | false | false |

**10. 我或你都可以（逻辑或操作符）**

逻辑或：`c=b>a || a>b`

逻辑或操作符表：

| A | B | A || B |
| -- | -- | -- |
| true | true | true |
| true | false | true |
| false | true | true |
| false | false | false |

**11. 是非颠倒（逻辑非操作符）**

逻辑非操作符：`!A`

逻辑非操作符值表：

| A | !A |
| -- | -- |
| true | false |
| false | true |

**12. 保持先后顺序（操作符优先级）**

乘法，除法的优先级比加法和减法的高

操作符之间的优先级：算术操作符>比较操作符>逻辑操作符>“=”赋值符号

**13. 编程练习**

---

第3章 一起组团（数组）
--

**1. 一起组团（什么是数组）**

一个数组可以存放多个数据

- 数组是值的集合
- 每一个值都有索引号，从0开始
- 每一个索引都有一个对应的值
- 可以根据需要添加更多的值

**2. 组团，并给团取个名（如何创建数组）**

创建数组：`var myarray = new Array();`

创建数组时候，还可以指定数组长度：`var myarray = new Array(8);`

注意：

- 创建的新数组是空数组时，输出时候显示 undefined
- 数组指定了长度后，实际上是可以变长的

**3. 谁是团里成员（数组赋值）**

给数组赋值：`myarr[0]=80;`

每一个值都有一个索引号，从0开始

还有两种简单的方法：

```
var myarray = new Array(1,2,3,4,5);
var myarray2 = [1,2,3,4,5];
```

数组可以存储任何类型的数据

**4. 团里添加新成员（向数组增加一个新元素）**

使用下一个未使用的索引，向数组新加一个新元素：`myarr[5] = 88;`

**5. 呼叫团里成员（使用数组元素）**

要得到一个数组元素的值，需要引用数组变量并提供一个索引：`myarr[0];`

**6. 了解成员数量（数组属性length）**

length属性表示数组的长度，即数组中元素的个数：`myarray.length;`

JS的数组的length是可变的：

```
var myarr = new Array(3);
myarr.length = 10;
```

一个数组的上下限分别是 0 和 length-1，数组随元素的增加，长度也会改变

**7. 二维数组**

二维数组的表示：`myarray[][]`，二维数组的索引也是从0开始

二维数组的定义方法一：

```
var myarr = new Array();  //先声明一维数组
for (var i=0;i<2;i++){
  myarr[i] = new Array();  //再声明二维数组
  for (var j=0;j<3;j++){
    myarr[i][j] = i+j;
  }
}
```

二维数组定义方法二：`var myarr = [[0,1,2],[1,2,3]];`

赋值：`myarr[0][1] = 5;`，其中，0表示行，1表示列

**8. 编程练习**

```
 <!DOCTYPE  HTML>
 <html >
 <head>
 <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
 <title>数组</title>
 <script type="text/javascript">
   //创建数组
   var  arr = ['*','##',"***","&&","****","##*"];
   arr[7] = "**";
   //显示数组长度
   document.write(arr.length + "<br/>");
   //将数组内容输出，完成达到的效果。
   var arr2 = ['*','**',"***","****"];
   for (var i=0;i<4;i++){
     document.write(arr2[i] + "<br/>");
   }
 </script>
 </head>
 <body>
 </body>
 </html>
```

---

第4章 跟着我的节奏走（流程控制语句）
--

**1. 做判断（if语句）**

基于条件成立才执行相应代码时使用的语句，语法：

```
if (条件)
{ 条件成立时候执行的代码 }
```

注意if需要小写，大写会出错

**2. 二选一（if...else语句）**

在指定的条件成立时候执行代码，条件不成立的时候执行else后面的代码，语法：

```
if(条件)
{ 条件成立时候执行的代码 }
else
{ 条件不成立时候执行的代码 }
```

**3. 多重判断（if...else嵌套语句）**

作用是在多组语句中选择一组来执行，语法：

```
if(条件1)
{ 条件1成立时执行的代码 }
else if(条件2)
{ 条件2成立时执行的代码 }
...
else if(条件n)
{ 条件n成立时执行的代码 }
else
{ 条件1到n都不成立时候执行的代码 }
```

**4. 多种选择（switch语句）**

选择多的时候switch比if else更加方便，语法：

```
switch(表达式)
{
case 值1:
  执行代码块1
  break;
case 值2:
  执行代码块2
  break;
...
case 值n:
  执行代码块n
  break;
default:
  与 case1，case2...casen不同时候执行的代码
}
```

说明：

- switch必须赋初始值，值和每一个case的值匹配
- break用来阻止运行下一个case，如果没有break，第一个匹配的case后面所有的case都会被执行
- 如果所有的case都不匹配，则运行default后面的语句

多个case可以写在一起：

```
switch (a)
{
case 1:
case 2:
  a等于1或2时候执行的语句
  break;
default:
  default语句
}
```

**5. 重复重复（for循环）**

for语句结构：

```
for (初始化变量;循环条件;循环迭代)
{
  循环语句
}
```

举例：

```
for(mymoney=1;mymoney<=10;mymoney++)
{ 
  sum= sum + mymoney;
}
```

**6. 反反复复（while循环）**

while循环重复执行一段代码，直到某个条件不再满足，语法：

```
while(判断条件)
{
  当判断条件为true时候的循环语句
}
```

**7. 来来回回（do...while循环）**

这个结构保证循环体至少运行一次，语法：

```
do
{
  判断条件为true的时候的循环语句
}
while(判断条件)
```

**8. 退出循环break**

while，for，do...while中，使用break退出当前循环，直接执行后面的代码，语法：

```
for(初始条件;判断条件;循环后条件值更新)
{
  if(特殊情况)
  {break;}
  循环代码
}
```

**9. 继续循环continue**

continue的作用是仅仅跳过本次循环，整体循环体继续执行，语法：

```
for(初始条件;判断条件;循环后条件值更新)
{
  if(特殊情况)
  {continue;}
  循环代码
}
```

**10. 编程练习**

在一个大学的编程选修课班里，我们得到了一组参加该班级的学生数据，分别是姓名、性别、年龄和年级，接下来呢，我们要利用JavaScript的知识挑出其中所有是大一的女生的的名字哦。

```
 <!DOCTYPE  HTML>
 <html >
 <head>
 <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
 <title>流程控制语句</title>
 <script type="text/javascript">
  //第一步把之前的数据写成一个数组的形式,定义变量为 infos
 var infos = [["小A","女",21,"大一"],["小B","男",23,"大三"],["小C","男",24,"大四"],["小D","女",21,"大一"],["小E","女",22,"大四"],["小F","男",21,"大一"],["小G","女",22,"大二"],["小H","女",20,"大三"],["小I","女",20,"大一"],["小J","男",20,"大三"]];
  //第一次筛选，找出都是大一的信息
 for (i=0;i<10;i++)
 {
   if (infos[i][3] == "大一")    
   { 
     //第二次筛选，找出都是女生的信息
     if (infos[i][1] == "女")
     {
         document.write(infos[i][0]+"<br/>");
     }
   } 
 } 
 </script>
 </head>
 <body>
 </body>
 </html> 
```

----

第5章 小程序，大作用（函数）
--

**1. 什么是函数**

函数：写一次代码，重复的使用，举例：

```
function add2(a,b){
  sum = a + b;
  alert(sum);
}  // 函数只要写一次
add2(3,4);
add2(7,8);  // 只要调用函数就可以
```

**2. 定义函数**

语法：

```
function 函数名()
{
  函数体;
}
```

**3. 函数调用**

直接在需要的位置写函数名来调用

在`<script>`标签中调用：

```
 <script type="text/javascript">
   function add2()
   {
     sum=1+1;
     alert(sum);
   } 
   add2();  // 调用函数
 </script>
```

在html中调用，通过点击按钮调用函数：

```
 <html>
 <head>
 <script type"text/javascript">
   function add()
   {
     sum=5+6;
     alert(sum);
   }
 </script>
 </head>
 <body>
   <form>
     <input type="button" value="click it" onclick="add2()">  // 按钮事件直接调用函数
   <form>
 </body>
 </html>
```

**4. 有参数的函数**

参数可以有多个，参数之间用逗号隔开。语法：

```
function 函数名(参数1,参数2)
{
  函数代码
}
```

**5. 返回值的函数**

用return来返回函数的值，语法：

```
function add2(x,y)
{
  sum=x+y;
  return sum;
}
```

函数的返回值可以是任何的类型

可以通过变量保存函数的返回值：`result = add2(3,4);`

**6. 编程练习**

写出一个函数：实现传入两个整数后弹出较大的整数。

```
 <!DOCTYPE  HTML>
 <html >
 <head>
 <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
 <title>函数</title>
 <script type="text/javascript">
 //定义函数
   function comp(a,b)
   {
     //函数体，判断两个整数比较的三种情况
     if ((a-b)>0){
       return a;
     }
     else if ((a-b) == 0){
       return "一样大";
     }
     else {
       return b;
     }
   } 
 //调用函数，实现下面两组数中，返回较大值。
   document.write(" 5 和 4 的较大值是:"+comp(5,4)+"<br>");
   document.write(" 6 和 3 的较大值是:"+comp(6,3)); 
 </script>
 </head>
 <body>
 </body>
 </html>
```

----

第6章 事件响应，让网页交互
--

**1. 什么是事件**

事件是可以被JS侦测到的行为，可以出发JS函数或程序。主要事件列表：

| 事件 | 说明 
| -- | -- |
| onclick | 鼠标点击事件 |
| onmouseover | 鼠标经过事件 |
| onmouseout | 鼠标移开事件 |
| onchange | 文本框内容改变事件 |
| onselect | 文本框内容被选中事件 |
| onfocus | 光标聚集 |
| onblur | 光标离开 |
| onload | 网页导入 |
| onunload | 网页关闭 |

**2. 鼠标点击事件（onclick）**

在网页上点击鼠标时执行的事件，一般和按钮一起使用，举例：

```
 ...
 <script type="text/javascript">
   function add2(){
     var sum = 1+2;
     document.write(sum);
   }
 </script>
 ...
 <input name="button" type="button" value="点击提交" onclick="add2()"/>
 ...
```

**3. 鼠标经过事件（onmouseover）**

鼠标移动到一个对象上的时候触发，举例：

```
<input name="button" type="button" value="点击提交" onmouseover="add2()"/>
```

**4. 鼠标移开事件（onmouseout）**

鼠标从当前对象移开时候触发，举例：

```
<input name="button" type="button" value="点击提交" onmouseout="add2()"/>
```

**5. 光标聚焦事件（onfocus）**

当网页中的对象获得焦点时候被触发，举例：

```
<input name="username" type="text" value="姓名" onfocus="add2()"/>
```

**6. 失焦事件（onblur）**

当光标移开当前获得焦点的对象的时候触发，举例：

```
<input name="username" type="text" value="姓名" onblur="add2()"/>
```

**7. 内容选中事件（onselect）**

当文本框或者文本域中的文字被选中时候触发，举例：

```
<input name="username" type="text" value="姓名" onselect="add2()"/>
```

**8. 文本框内容改变事件（onchange）**

改变文本框内容会触发onchange事件，举例：

```
<input name="username" type="text" value="姓名" onchange="add2()"/>
```

**9. 加载事件（onload）**

事件在页面加载完成后立即发生，注意：

- 加载页面时，触发onload事件，事件写在`<body>`标签内
- 加载页面可以理解为打开一个新页面时

举例：

```
 <head>
 ...
 <script type="text/javascript">
   function message(){
     alert("加载中，请稍后");
   }
 </script>
 ...
 </head>
 <body onload="message()">
   ...
 </body>
```

**10. 卸载事件（onunload）**

退出页面时（包括页面关闭，页面刷新等）被触发，注意：

- 不同浏览器对onunload的支持不同

举例：

```
 <head>
 ...
 <script type="text/javascript">
   window.onunload = onunload_message;
   function onunload_message(){
     alert("确定离开本页吗？");
   }
 </script>
 </head>
```

**11. 编程练习**

使用JS完成一个简单的计算器功能。实现2个输入框中输入整数后，点击第三个输入框能给出2个整数的加减乘除。

```
 <!DOCTYPE html>
 <html>
   <head>
     <title>事件</title>  
     <script type="text/javascript">
       function count(){
         var num;
         //获取第一个输入框的值
         var num1 = document.getElementById("txt1").value;
         //获取第二个输入框的值
         var num2 = document.getElementById("txt2").value;
         //获取选择框的值
         var select_value = document.getElementById("select").options[document.getElementById("select").selectedIndex].value;
         //获取通过下拉框来选择的值来改变加减乘除的运算法则
         switch (select_value){
           case "+":
             num=parseInt(num1)+parseInt(num2);
             break;
           case "-":
             num=num1-num2;
             break;
           case "*":
             num=num1*num2;
             break;
           case "/":
             num=num1/num2;
             break;
         }
         //设置结果输入框的值 
         document.getElementById("fruit").value = num;
       }
     </script> 
   </head> 
 <body>
   <input type='text' id='txt1'/> 
   <select id='select'>
     <option value='+'>+</option>
     <option value="-">-</option>
     <option value="*">*</option>
     <option value="/">/</option>
   </select>
   <input type='text' id='txt2' /> 
   <input type='button' value=' = ' onclick="count()"/> <!--通过 = 按钮来调用创建的函数，得到结果--> 
   <input type='text' id='fruit' />   
   </body>
 </html>
```

----

第7章 JavaScript内置对象
--

**1. 什么是对象**

JavaScript中的所有事物都是对象，每个对象有属性和方法

- 属性：反应对象的某些特定的性质
- 方法：能够在对象上执行的操作

JS有多个内建对象，如String，Date，Array等，定义对象：

```
var objectName = new Array();  // 使用new关键字定义对象
var objectName = [];
```

访问对象属性：`objectName.propertyName`

如获取数组长度：

```
var myArray = new Array(6);
var myl = myArray.length;  // 访问数组长度的length属性
```

访问对象方法：`objectName.methodName()`

如将文本转换为大写：

```
var myStr = "Hello World!";
var request = myStr.toUpperCase();  // 使用字符串对象方法
```

**2. Date日期对象**

日期对象可以存储日期，时间精确到毫秒，定义：`var Udate = new Date();`

日期对象的默认初始值是当前时间（电脑系统时间），可以定义初始值：

```
var d = new Date(2012 ,10 ,1);  // 2012年10月1日
var d = new Date('Oct 1, 2012');
```

严格的定义时间的方法：

| 方法名称 | 功能描述 |
| -- | -- |
| get/setDate() | 返回/设置日期 |
| get/setFullYear() | 返回/设置年份，四位数表示 |
| get/setYear() | 返回/设置年份 |
| get/setMonth() | 返回/设置月份，0-一月，1-二月...11-十二月 |
| get/setDay() | 返回/设置星期，0-星期天 |
| get/setHours() | 返回/设置小时，24小时制 |
| get/setMinutes() | 返回/设置分钟数 |
| get/setSeconds() | 返回/设置秒钟数 |
| get/setTime() | 返回/设置时间（毫秒为单位） |

**3. 返回/设置年份方法**

输出当前年份：`myDate.getFullYear();`，返回为2015

设置年份：`myDate.setFullYear(81);`，返回81或0081，不同浏览器返回不同

不同浏览器的时间格式会有差异

**4. 返回星期方法**

可以通过getDay()配合数组来获取星期：

```
var weekday = ["星期日","星期一","星期二","星期三","星期四","星期五","星期六"];
var myNum = myDate.getDay();
document.write(weekday[myNum]);
```

**5. 返回/设置时间方法**

get/setTime 单位是毫秒数，计算从1970年1月1日零时到日期对象所指的日期的毫秒数

如计算当前时间推迟1小时的时间：

```
var myDate = new Date();
myDate.setTime(myDate.getTime() + 60*60*1000 );
```

**6. String字符串对象**

```
var myStr = "I love JS!";  // 定义字符串对象
var myl = myStr.length;  // 访问字符串属性，返回字符串的长度
myStr.toUpperCase();  // 访问字符串方法，将小写字母转换成大写
```

**7. 返回指定位置的字符**

使用 chatAt() 来返回指定位置的字符：`stringObject.charAt(index)`

index是字符在字符串中的下标，注意：

- 第一个字符的下标是0
- 如果参数不在0和string.length-1之间，会返回空字符串
- 空格也算一个字符

**8. 返回指定的字符串首次出现的位置**

使用 indexOf() 返回某个指定字符串在字符串中首次出现的位置：`stringObject.indexOf(substring, startpos)`



