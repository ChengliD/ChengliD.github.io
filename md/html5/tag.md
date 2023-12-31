## 一、常用标签
### 1.1、标题标签
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

### 1.2、段落标签
&emsp;&emsp;一般用在新闻段落、文章段落、产品描述信息等等

&emsp;&emsp;标签名：p（双标签）

&emsp;&emsp;显示特点：

&emsp;&emsp;&emsp;&emsp;1、独占一行
<br>
&emsp;&emsp;&emsp;&emsp;2、段落之间存在间隙

### 1.3、换行标签
&emsp;&emsp;标签名：br（单标签）

&emsp;&emsp;说明：

&emsp;&emsp;&emsp;&emsp;浏览器不能识别代码中的Enter键换行

### 1.4、水平线标签
&emsp;&emsp;标签名：hr（单标签）

### 1.5、文本格式化标签
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


### 1.6、图像标签
&emsp;&emsp;在网页中插入图片

&emsp;&emsp;标签名: img（单标签）

| 属性    | 作用    | 说明                   |
|-------|-------|----------------------|
| src   | 加粗    | 用来指定图像的位置和名称，必须要有该属性 |
| alt   | 替换文本  | 图片无法显示的时候显示的文字       |
| title | 提示文本  | 鼠标悬停在图片上面的时候显示的文字    |
| width | 图片的宽度 | 值为数字，没有单位            |
| height | 图片的高度 | 值为数字，没有单位            |

&emsp;&emsp;填写属性的格式为：属性名=“属性值”
<br>
&emsp;&emsp;属性名要写在尖括号里面，标签名后面，各个属性之间用空格分割开，不区分前后顺序

### 1.7、超链接标签
&emsp;&emsp;标签名: a（双标签）

&emsp;&emsp;说明：
<br>
&emsp;&emsp;&emsp;&emsp;1、href属性值是跳转地址，是超链接的必须属性
<br>
&emsp;&emsp;&emsp;&emsp;2、超链接默认是在当前窗口跳转页面，添加target="_blank"实现新窗口打开页面
<br>
&emsp;&emsp;&emsp;&emsp;3、开发初期，不确定跳转地址，则href属性值写为#，表示空链接，页面不会跳转

### 1.8、音频标签
&emsp;&emsp;标签名: audio（双标签）

| 属性         | 作用       | 说明                |
|------------|----------|-------------------|
| src(必须属性)  | 音频URL    | 支持格式：MP3、Ogg、Wav  |
| controls   | 显示音频控制面板 |                   |
| loop       | 循环播放     |                   |
| autoplay   | 自动播放    |为了提升用户体验，浏览器一般会禁用自动播放功能         |

在书写HTML5属性时，如果属性名和属性值相同，可以简写为一个单词

### 1.9、视频标签
&emsp;&emsp;标签名: video（双标签）

| 属性        | 作用       | 说明                      |
|-----------|----------|-------------------------|
| src(必须属性) | 视频URL    | 支持格式：MP4、WebM、Ogg       |
| controls  | 显示视频控制面板 |                         |
| loop      | 循环播放     |                         |
| muted     | 静音播放     |                         |
| autoplay  | 自动播放     | 为了提升用户体验，浏览器支持在静音状态自动播放 |


### 1.10、列表
#### 1.10.1、无序列表

作用：布局排列整齐的不需要规定顺序的区域

标签：ul嵌套li，ul是无序列表，li是列表条目

![](../../imgs/html5/tag_1.png)

注意事项：
<br>
&emsp;&emsp;ul标签里面只能包裹li标签
<br>
&emsp;&emsp;li标签里面可以包裹任何内容


#### 1.10.2、有序列表

作用：布局排列整齐的需要规定顺序的区域

标签：ol嵌套li，ol是有序列表，li是列表条目

![](../../imgs/html5/tag_2.png)

注意事项：
<br>
&emsp;&emsp;ol标签里面只能包裹li标签
<br>
&emsp;&emsp;li标签里面可以包裹任何内容


#### 1.10.3、定义列表
&emsp;&emsp;标签：dl嵌套dt和dd，dl是定义列表，dt是定义列表的标题，dd是定义列表的描述/详情

![](../../imgs/html5/tag_3.png)

注意事项：
<br>
&emsp;&emsp;dl里面只能包含dt和dd
<br>
&emsp;&emsp;dt和dd里面可以包含任何内容

### 1.11、表格
#### 1.11.1、表格标签
网页中的表格与Excel表格相似，用来展示数据。

标签：table嵌套tr，tr嵌套td/th

![](../../imgs/html5/tag_4.png)

提示：在网页中，表格默认没有边框线，使用border属性可以为表格添加边框线
#### 1.11.2、表格结构标签
作用：用表格结构标签把内容划分区域，让表格结构更清晰，语义更清晰

![](../../imgs/html5/tag_5.png)

提示：表格结构标签可以省略

#### 1.11.3、合并单元格
作用：将多个单元格合并成一个单元格，以合并同类信息

合并单元格的步骤：
<br>
1、明确合并的目标
<br>
2、保留最左最上的单元格，添加属性（取值是数字，表示需要合并的单元格数量）
<br>
&emsp;– 跨行合并，保留最上单元格，添加属性 rowspan
<br>
&emsp;– 跨列合并，保留最左单元格，添加属性 colspan
<br>
3、删除其他单元格
   注意：不能跨表格结构标签合并单元格（thead、tbody、tfoot）

### 1.12、表单
&emsp;&emsp;作用：收集用户信息

&emsp;&emsp;使用场景
<br>
&emsp;&emsp;&emsp;&emsp;登录页面
<br>
&emsp;&emsp;&emsp;&emsp;注册页面
<br>
&emsp;&emsp;&emsp;&emsp;搜索区域

&emsp;&emsp;标签名：input（单标签）

| 属性名         | 属性值     | 作用          |
|-------------|---------|-------------|
| type(必须属性)  | text    | 文本框，用于输入单行文本 |
|             | password | 密码框         |
|             | radio   | 单选框         |
|             | checkbox | 多选框         |
|             | file    | 上传文件        |
 | placeholder | 提示信息    | 文本框和密码框可以使用 |

#### 1.12.1、单选框
![](../../imgs/html5/tag_6.png)

&emsp;name相同的多个单选框称为一组单选框，这组单选框保证了单选的功能
#### 1.12.2、上传文件
默认情况下，文件上传表单控件只能上传一个文件，添加multiple属性可以实现文件多选功能

#### 1.12.3、多选框
如果想要多选框默认选中，则添加checked选项

### 1.13、下拉菜单
标签：select嵌套option，select是下拉菜单整体，option是下拉菜单的每一项

![](../../imgs/html5/tag_7.png)

默认显示第一项，selected属性实现默认选中功能

### 1.14、文本域
&emsp;&emsp;作用：多行输入文本的表单控件

&emsp;&emsp;标签名：textarea（双标签）

&emsp;&emsp;注意点：
<br>
&emsp;&emsp;&emsp;&emsp;实际开发中，使用 CSS 设置 文本域的尺寸
<br>
&emsp;&emsp;&emsp;&emsp;实际开发中，一般禁用右下角的拖拽功能


