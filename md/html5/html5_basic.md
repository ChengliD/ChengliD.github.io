# <Central>HTML5基础</Central>

## 一、HTML概念
&emsp;&emsp;HTML 超文本标记语言——HyperText Markup Language。
<br>
&emsp;&emsp;超文本是什么？ 链接
<br>
&emsp;&emsp;标记是什么？   标记也叫标签，带尖括号的文本


## 二、标签语法
&emsp;&emsp;标签成对出现，中间包裹内容<>里面放英文字母（标签名），结束标签的前面比开始标签多 /
<br>
&emsp;&emsp;拓展：
<br>
&emsp;&emsp;&emsp;双标签：成对出现的标签
<br>
&emsp;&emsp;&emsp;单标签：只有开始标签，没有结束标签


## 三、HTML基本骨架
<img src="../../imgs/html5/html5_basic_1.png">

html：整个网页
<br>
head：网页头部，用来存放给浏览器看的信息，例如CSS
<br>
&emsp;title：网页标题
<br>
body：网页主体，用来存放给用户看的信息，例如图片、文字


## 四、标签的关系
作用：明确标签的书写位置，让代码格式更整齐

父子关系（嵌套关系）:

&emsp;&emsp;<img src="../../imgs/html5/html5_basic_2.png">

兄弟关系（并列关系）:

&emsp;&emsp;<img src="../../imgs/html5/html5_basic_3.png">

<strong>代码格式</strong>

&emsp;父子关系：子级标签换行且缩进（Tab键）

&emsp;兄弟关系：兄弟标签换行要对齐


## 五、注释
&emsp;&emsp;注释就是对代码的解释和说明，其目的是让人们能够更加轻松地了解代码。注释是编写程序时，写程序的人给一个语句、程序段、函数等的解释或提示，能提高程序代码的可读性。

&emsp;&emsp;在编写HTML代码时，我们经常要在一些关键代码旁做一下注释，这样的好处很多，比如：方便理解、方便查找或方便项目组里的其他程序员了解你的代码，而且可以方便以后你对自己代码进行修改。

&emsp;&emsp;<!--  内容   -- >注释标签用来在源文档中插入注释，注释不会在浏览器中显示。


## 六、常用标签
### 6.1、标题标签
&emsp;&emsp;一般用在新闻标题、文章标题、网页区域名称、产品名称等

&emsp;&emsp;标签名：h1 - h6（双标签）

&emsp;&emsp;显示特点：

&emsp;&emsp;&emsp;&emsp;1、文字加粗
<br>
&emsp;&emsp;&emsp;&emsp;2、字号逐渐减小
<br>
&emsp;&emsp;&emsp;&emsp;3、独占一行（换行）

&emsp;&emsp;说明：

&emsp;&emsp;&emsp;&emsp;1、h1标签在一个网页中只能用一次，用来放新闻标题或网页的logo
<br>
&emsp;&emsp;&emsp;&emsp;2、h2~h6没有使用次数的限制

### 6.2、段落标签
&emsp;&emsp;一般用在新闻段落、文章段落、产品描述信息等等

&emsp;&emsp;标签名：p（双标签）

&emsp;&emsp;显示特点：

&emsp;&emsp;&emsp;&emsp;1、独占一行
<br>
&emsp;&emsp;&emsp;&emsp;2、段落之间存在间隙

### 6.3、换行标签
&emsp;&emsp;标签名：br（单标签）

&emsp;&emsp;说明：

&emsp;&emsp;&emsp;&emsp;浏览器不能识别代码中的Enter键换行

### 6.4、水平线标签
&emsp;&emsp;标签名：hr（单标签）

### 6.5、文本格式化标签
&emsp;&emsp;为文本添加特殊格式，以突出重点。常见的文本格式：加粗、倾斜、下划线、删除线等

&emsp;&emsp;标签的主要部分有：

&emsp;&emsp;&emsp;&emsp;开始标签：包含元素的名称，被左、右角括号所包围。表示元素从这里开始或开始起作用
<br>
&emsp;&emsp;&emsp;&emsp;结束标签：与开始标签相似，只是其在元素名之前包含了一个斜杠。这表示着元素的结尾
<br>
&emsp;&emsp;&emsp;&emsp;内容：元素的内容


| 标签名    |  效果  |
|--------|------|
| strong | 加粗   |
| em     | 倾斜 | 
| ins    | 下划线  |
| del    | 删除线  |







