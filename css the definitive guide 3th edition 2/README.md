# 选择器
---
## 基本规则
---
每个规则有两个基本部分：选择器和声明块。声明块由一个或多个声明组成，每个声明是一个属性——值对。每个样式表由一系列规则组成。
![image](https://raw.githubusercontent.com/huangjingxing/css-notes/master/css%20the%20definitive%20guide%203th%20edition%202/photos/1.png)

## 元素选择器
---
最常见的CSS选择器是HTML元素。
```
html {color: black;}
p {color: gray;}
h2 {color: silver;}
```
## 声明和关键字
---
声明总有如下格式：一个属性后面跟一个冒号，再后面是一个值，然后是一个分号。冒号和分号后面可以有0个或多个空格。
声明使用了不正确的属性或值，整个声明会被忽略。
如果一个属性的值取多个关键字，关键字通常由空格分隔。
```
p{font:medium Helvetica;} 
```
CSS关键字不用空格分隔的例外：在font属性中有一种情况可使用斜线分隔两个特定关键字。
```
h2{font:large/150% sans-serif;}  
```
## 分组
 ---
### 选择器分组
```
h2,p {color:gray;} 
```
将规则应用于这两个元素,这样使书写更容易
### 通配选择器
CSS2引入的通配选择器显示为一个星号（*），它可以与任何元素匹配。
```
*{color:red;}  
```
方便但有后果。
### 声明分组
将多个声明写为一组。
```
h1{
font:18px Helvetica;
color: purple;
background:aqua;
}  
```
每个声明后要有分号，此处易错。
### 结合选择器和声明的分组
```
h1, h2, h3, h4, h5, h6 {
color: gray; 
background: white; 
padding: 0.5em;
  border: 1px solid black; 
font-family: Charcoal,sans-serif;
}
```

## 类选择器和ID选择器
 ---
它们允许以一种独立于文档元素的方式来指定样式
### 类选择器
应用样式而不考虑具体涉及的元素时，常用类选择器。类名前有一个点号（.）。
```
*.warning{font-weight:bold;}  
```
标记所有类属性为warning的元素；通配选择器可以忽略。
```
p.warning{font-weight:bold;}  
```
标记所有类属性为warning的段落。
### 多类选择器
```
.warning.urgent{background:silver;}  
```
两个类选择器链接在一起，仅可以选择同时包含这些类名的元素，顺序不限。
### ID选择器
与类选择器类似，但有重要的差别。ID选择器前面是一个#号，引用的是id属性的值。
```
#lead-para{font-weight:bold;}  
```
### 类选择器还是ID选择器？
同一文档中每个元素的ID是唯一的，因此ID选择器仅能使用一次。ID选择器不能结合使用。ID值是大小写敏感的。

## 属性选择器
 ---
### 简单属性选择
选择有class属性（值不限）的所有h1元素：
```
h1[class]{color:silver;}  
```
可将属性选择器链接在一起，例如同时将有href和title属性的HTML超链接的文本置为粗体：
```
a[href][title]{font-weight:bold;}  
```
### 根据具体属性值选择
例如将指向Web服务器上某个特定文档的超链接变为粗体：
```
a[href="http://www.css-discuss.org/about.html"]{font-weight:bold;}  
```
多个属性-值选择器链接在一起：
```
a[href="http://www.w3.org/"][title="W3CHome"]{font-size:200%;}  
```
注意，这种格式要求必须与属性值完全匹配；ID选择器与指定id属性的属性选择器不相同。
### 根据部分属性值选择
选择class属性中包含warning的元素，可用属性选择器：
```
p[class~="warning"]{font-weight:bold;}  
```
波浪号是部分选择的关键，根据属性值中出现的一个用空格分隔的词来完成选择。当属性是class时，p.warning与p[class~="warning"]相同。
### 子串匹配属性选择器：
 
>* [foo^="bar"]选择foo属性值以“bar”开头的所有元素
>* [foo$="bar"]选择foo属性值以“bar”结尾的所有元素
>* [foo*="bar"]选择foo属性值中包含子串“bar”的所有元素

### 特定属性选择类型
```
*{lang |= “en”}{color:silver;}
```
这个规则会选择lang属性等于en或者以en-开头的所有元素。这种属性选择器最常见的用途是匹配语言值。  
## 使用文档结构
 ---
### 理解父子关系

 
如果一个元素出现在文档层次结构中另一个元素的上一层，则称前者是后者的父元素。
一个元素出现在另一个元素的下一层，则称前者是后者的子元素。
如果两元素路径要经过两层或多层，这些元素则有祖先-后代关系，而不是父子关系。
 ![image](https://raw.githubusercontent.com/huangjingxing/css-notes/master/css%20the%20definitive%20guide%203th%20edition%202/photos/2.png)

### 后代选择器
 
也叫包含选择器。与h1元素中包含的em元素匹配的规则：
```
h1 em{color:gray;}  
blockquote b,p b{color:gray;}  
```
不仅限于两个选择器：
```
ul ol ul em{color:gray;}  
```
两个元素之间的层次间隔可以是无限的，并不一定是父子。

### 选择子元素
 
只选择子元素而不选择其他后代元素，可使用子结合符，即大于号：
```
h1>strong{color:red;} 
```
### 选择相邻兄弟元素
 
要选择紧接在另一个元素后的元素，而且二者有相同的父元素，可以使用相邻兄弟结合符，这表示为一个加号（+）。
强调：不是选择两个元素，而是选择后一个元素。

```
h1+p{margin-top:0}  
```
## 伪类和伪元素
 ---
伪类对元素进行分类是基于特征而不是它们的名字、属性或者内容；原则上特征是不可以从文档树上推断得到的。
利用伪类选择器和伪元素选择器，可以为文档中不一定具体存在的结构指定样式，或者为某些元素的状态所指示的幻像类指定样式。
### 伪类选择器
比如处理已访问和未访问的链接的样式，不必在每次访问后修改锚的类，CSS定义了伪类使已访问页面的锚好像已有了一个visited类：
```
p[class~="warning"]{font-weight:bold;}  
```
冒号（：）是伪元素的名片，所有伪类和伪元素关键字前面都有一个冒号。
  >* 链接伪类
:link指示作为超链接（即有一个href属性）并指向一个未访问地址的所有锚。包括已访问和未访问的超链接。
:visited指示作为已访问地址超链接的所有锚。
这两个伪类是静态伪类。
>* 动态伪类
:focus指示当前拥有输入焦点的元素，即接受键盘输入或能以某种方式激活的元素
:hover指示鼠标指针当前停留的元素
:active指示被用户输入激活的元素
多行伪类规则并列时，伪类的顺序很重要。下一章将解释。
>* 动态样式的实际问题
使用动态伪类时，可能会改变页面布局。但CSS规范指出，文档第一次显示之后，用户代理不必重绘文档。
不要指望预想的效果肯定会发生。
>* 选择第一个子元素
静态伪类first-child来选择元素的第一个子元素。
```
p:first-child{font-weight:bold;}  
```
此例不是选择p元素的第一个子元素，是选择作为其父元素的第一个子元素的p元素。
>* 根据语言选择
需要根据元素的语言选择时，可使用lang()伪类。把所有法语元素变成斜体：

```
*:lang(fr){font-style:italic;}  
```
在需要语言特定的样式时，多数情况下伪类是更好的选择。
>* 结合伪类
同一个选择器可结合使用伪类。伪类结合时，顺序指定不重要。注意不要使用互斥的伪类。
```
a:link:hover:lang(de){color:gray;}
```
### 伪元素选择器
 
>* 设置首字母样式
每一段的首字母变为红色：
```
p:first-letter{color:red;} 
```

>* 设置第一行的样式
一个文档中第一段第一行变为紫色：
```
p:first-line{color:purple;}  

```

>* :first-letter和:first-line的限制
伪元素所允许的属性：
 >* 设置之前和之后元素的样式
每个h2元素前加一对银色中括号：
```

h2.before{content:"}}";color:silver;}  
```

文档的最后的结束语：
```

body:after{content:"The end.";}  
```
