## 字体
---
### 字体系列
除了各种特定字体系列（如Times、Verdana、Helvetica或Arial）外，还定义了5种通用字体系列。
Serif
Sans-serif
Monospace
Cursive
Fantasy
理论上，用户安装的字体通常会落入到上述某种通用系列中。

### 使用通用字体系列
可使用属性font-family在文档中采用上述任何字体系列。该属性有继承性。
```
body{font-family:sans-serif;}
```
用户代理会从该系列选择一个字体。

### 指定字体系列
```
h1{font-family:Georgia;}
```
如果用户代理找不到Georgia会使用默认字体。
```
h1{font-family:Georgia,serif;}
```
如果没有安装Georgia，会使用serif字体。

建议在font-family中提供通用字体系列作为有效的候补策略。

### 使用引号
只有当一个字体名中有一个或多个空格，或者字体名包括#或$之类的符号，才需在font-family声明中加引号。
```
<p style="font-family:'New CenturySchoolbook',Times,serif;">……</p>
```

### 字体加粗
可以使用字体系列中粗的字体，更建议的是使用font-weight。

### 加粗如何起作用
有100~900共9级加粗度，但不一定每级加粗度的粗细都不同。400等价于normal，700等价于bold。

### 让字体更粗
使用bolder可以增加加粗度。

### 让字体更细
使用lighter可以减小加粗度。

### 字体大小
font-size的作用是为给定字体的em框提供大小。

### 绝对大小
有7个绝对大小值：xx-small、x=small、small、medium、large、x-large和xx-large。这些关键字没有明确定义，而是相对地定义。

### 相对大小
larger或smaller使元素的大小相对于其父元素的大小在绝对大小梯度上上移或下移。移动后可以超过绝对大小范围。

### 百分数和大小
百分数值总是根据从父元素继承的大小来计算。用户代理会将百分数计算取整。

### 字体大小和继承
继承是对于父元素来说的，可以逐级继承。由于用户代理会将百分数计算取整，多层继承可能会使取整错误积累。

### 使用长度单位
即上一章提到的长度单位。

### 风格和变形
### 有风格的字体
font-style的值有italic（形如手写体的斜体）、oblique（倾斜）、normal、inherit。具有继承性。

### 字体变形
font-variant的值有small-caps、normal、inherit。具有继承性。

### 拉伸和调整字体
font-stretch的值有normal、wider、narrow、ultra-condensed、extra-condensed、condensed、semi-condensed、semi-expanded、expanded、extra-expanded、ultra-expanded、inherit。具有继承性。

font-size-adjust的值有<number>、none、inherit。具有继承性。声明的font-size×（font-size-adjust值÷可用字体的方面值）=调整后的font-size。

### font属性
font属性具有继承性。按如下顺序设置：
font-style
font-variant
font-weight
font-size/line-height
font-family
其他值：caption、icon、menu、message-box、small-caption、status-bar、inherit
### 增加行高
line-height是文本属性而不是字体属性。可作为对font-size的补充，写在后面并用斜线（/）与之分隔。

body{font-size:12px;}

h2{font:bold italic 200%/1.2 Verdana,Helvetica,Arial,sans-serif;}

### 适当地使用简写
在使用简写属性font时，所有被忽略的值都会重置为其默认值。

### 使用系统字体
以下属性会获取操作系统的字体设置。

caption：用于有标题的控件，如按钮。
icon：用于对图标加标签。
menu：用于菜单。
message-box：用于对话框。
small-caption：用于对小控件加标签。
status-bar：用于窗口状态条。
字体匹配
### 智能字体匹配
写出以下规则，

@font-face{font-style:normal;font-family:"Times";slope:-5;}

用户代理会找到最接近描述的serif normal字体。

### 字体下载
用户代理可以在文档中下载一个远程字体：

@font-face{font-family:"ScarboroughFair";src:url(http://www.example.com/fonts/ps/scarborough.ps);}

字体传输需要时间。
