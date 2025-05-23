---
title: "html5笔记 基础标签"
meta_title: ""
description: "html5笔记 基础标签"
date: 2025-05-21T05:00:00Z
image: "/images/gallery/01.jpg"
categories: ["html", "markdown"]
author: "ruiyu"
tags: ["html", "markdown"]
draft: false
---



# 一、基础标签

## 1.img

```html
<img src="" width="" alt="">
```


* img标签中的img其实是英文image的缩写
  * 所以img标签的作用, 就是告诉浏览器我们需要显示一张图片

* img标签格式: <img src="">
  * 其实img标签中的src是英文source的缩写
  * 所以img标签中的src就是用来告诉img标签, 需要显示的图片名称

* 注意点

  - 和H系列标签/p标签还有Hr标签不一样, img标签不会独占一行

  - 如果我们手动指定了img标签显示的图片的宽度和高度, 有可能会导致图片变形, 那么如果又想指定宽度和高度, 又不想让图片变形. 我们可以只指定宽度和高度其中的一个值即可

  - 只要指定了高度, 系统会自动根据高度计算出宽度, 只要指定了宽度, 系统会自动根据宽度计算出高度, 并且都是等比拉伸的, 也就是说不会变形


* img中的其它属性
  * width: 宽度
  * height: 高度
    * 所以在img标签中width/height这两个属性的作用, 就是用来告诉img标签将来需要显示的图片有多宽有多高
    * 如果img标签没有指定需要显示的图片的宽高, 那么系统会按照图片默认的宽高来显示
    * 如果img标签指定的宽高, 那么系统会按照指定的宽高来显示
  * title: 用于告诉浏览器, 当鼠标悬停在图片上时, 需要弹出的描述框中显示什么内容
  
  * alt其实是英文**alternate**的缩写, 它的作用就是用于告诉浏览器, 当需要显示的图片找不到时显示什么内容
  

## 2.br

* br标签, 如何在HTML中换行? 可以使用br标签
  1. br标签作用: 换行
  1. br标签格式: <br>
  3. br标签的注意点:
     3.1多个br标签可以连续使用, 使用了多少个br标签就会换多少行
     3.2由于HTML的作用就是用来给文本添加语义, 而br标签的语义是不另起一个段落换行, 而在企业开发中一般情况下需要换行都是因为需要另起一个段落, 所以在企业开发中很少使用br标签


## 3.src="路径问题"

* 路径问题

  * 其实想给src属性赋值有两种方式
    1. 通过相对路径赋值(掌握)
       * 相对路径就是每次都从.html文件所在的文件夹开始查找, 我们称之为相对路径

### 相对路径的使用

* 同级

  * 同级就是"图片"和".html文件"存储在同一个文件夹中

  * 格式: 
    ```css
    src="QRCode.jpg"
    ```

  * 含义: 在.html文件所在的文件夹中查找名称叫做QRCode.jpg的图片
  
    



* 下级

   * 下级就是"存储图片的文件夹"和".html文件"在同一个文件夹中

   * 格式: 

     ```css
     src="images/QRCode.jpg"
     ```

   * 含义: 在.html文件所在的文件夹中找到名称叫做images的文件夹,然后再在images文件夹中找到名称叫做QRCode.jpg的图片



 * 上级

   * 上级就是"存储图片的位置"和存"储代码的文件夹"在同一个文件夹中

   * 格式:
     ```css
      src="../QRCode.jpg"
     ```
   
   * 含义：在.html文件所在的文件夹中找到这个文件夹的上一级文件夹, 然后再在上一级文件夹中找到名称叫做QRCode.jpg
     其中../代表找到当前文件夹的上一级文件夹



### 2. 通过绝对路径赋值(了解)

* 绝对路径就是每次都从指定的盘符开始查找
  * 格式: src="C:\Users\Jonathan_Lee\Desktop\HTML基础\QRCode.jpg"
  * 含义: 在C盘下找到Users文件夹, 然后在Users文件夹中找到Jonathan_Lee文件夹, 然后在Jonathan_Lee文件夹中找到Desktop文件夹, 然后在Desktop文件夹中找到HTML基础文件夹, 然后在HTML基础文件夹中找到名称叫做QRCode.jpg的图片

* 注意:
  1. 路径中不要出现中文, 否则可能出现未知问题
  2. 如果是通过"相对路径"来指定图片, 不能跨盘符
     2.1 例如.html文件在C盘, 那么不能去查找D盘图片

## 4. a标签
```html
<a href="" target="_blank/_self" title=""></a>
```

* 什么是a标签?

  * a标签的作用: 就是用于控制页面与页面之间跳转的

    * a标签的格式: 
      ```html
      <a href="指定需要跳转的目标界面">需要展现给用户查看的内容</a>
      ```

      

* a标签中有一个叫做target属性, 这个属性的作用就是专门用于控制如何跳转
  * _self: 用于在当前选项卡中跳转, 也就是不新建界面跳转. 默认就是_self
  * _blank: 用于在新的选项卡中跳转, 也就是新建界面跳转

* a标签中还有一个属性,
  * 叫做title. a标签中的title和img标签中的title一样, 都是用来控制鼠标悬停时显示的提示文本的

* 注意点:
  1. a标签不仅可以让文字可以点击, 还可以让图片也能够被点击
  2. 一个a标签必须有一个href属性, 否则a标签不知道要跳转到什么地方
  3. 如果通过a标签的href属性指定一个URL地址, 那么必须在地址前面加上http://或https://
  4. a标签的href属性除了可以指定一个网络地址以外, 还可以指定一个本地地址

## 5. base标签

```html
<base target="_blank">
<!--
base标签就是专门用来统一的指定当前网页中所有的超链接(a标签)需要如何打开

注意点:
1.base标签必须写在head标签的开始标签和结束标签之间
2.如果既在base中指定了target又在a标签中指定了target,那么浏览器会按照a标签中指定的来执行
-->
```



## 6.假链接

1. 什么是假链接?
   * 就是点击之后不会跳转的链接我们称之为假链接

2. 假链接存在的意义:
   * 在企业开发前期, 其它界面都没有写出来, 那么我们就不知道应该跳转到什么地方, 所以就只能使用假链接来代替. 当项目后期其它界面都已经完成时再将假链接体会为真链接

3. 假链接的格式:
   1.#
   2.javascript:

4. 两者之间的区别:
   * #的假链接会自动回到网页的顶部
   * javascript:的假链接不会自动回到网页顶部

# 二、列表标签



1. 什么是列表标签?
   * 列表标签的作用: 给一堆数据添加列表语义, 也就是告诉搜索引擎告诉浏览器这一堆数据是一个整体

2. HTML中列表标签的分类
   2.1无序列表(最多)(unordered list)
   2.2有序列表(最少)(ordered list)
   2.3定义列表(其次)(definition list)

## 1. 无序列表

```html
<ul>
    <li>广州</li>
    <li>北京</li>
    <li>上海</li>
    <li>武汉</li>
</ul>
```

显示如下：

<ul>
    <li>广州</li>
    <li>北京</li>
    <li>上海</li>
    <li>武汉</li>
</ul>


### 1.1 无序列表作用:

* 给一堆数据添加列表语义, 并且这一堆数据中所有的数据都没有先后之分
  * 什么叫有先后之分?
    * 例如: 排行榜
  * 什么叫没有先后之分?
    * 例如: 中国有哪些城市

### 1.2 无序列表格式:

```html
<ul>
    <li>需要显示的条目内容</li>
    <li>需要显示的条目内容</li>
</ul>
```

显示如下：

<ul>
    <li>需要显示的条目内容</li>
        <li>需要显示的条目内容</li>
</ul>

分析：

* li其实是英文list item的缩写
* list是列表的意思
* item是条目的意思
* 所以结合起来就是 列表条目的意思

### 1.3 无序列表注意点:

1. 一定要记住ul标签是用来给一堆数据添加列表语义的, 而不是用来给他们添加小圆点的
2. ul标签和li标签是一个整体, 是一个组合. 所以一般情况下ul标签和li标签都是一起出现, 不会单个出现. 也就是说不会单独使用一个ul标签或者单独使用一个li 标签, 都是结合在一起使用
3. 由于ul标签和li标签是一个组合, 所以ul标签中不推荐包含其它标签, 也就是说以后你在ul标签中只会看到li标签

* 无序列表应用场景:
  1. 新闻列表
  2. 商品列表
  3. 导航条

* 在企业开发中, li标签中的内容可能会很复杂, 所以我们可以继续在li标签中添加其它的标签来丰富我的界面
  
* 总结:
  1. 一定更要记住ul标签中最好只放li标签
  2. 但是li标签中还可以继续放其它的标签
  3. webstrom 快速书写
     ul>li*(4)

## 2.有序列表

```html
<ol>
    <li></li>
    <li></li>
    <li></li>
</ol>
```

显示如下

* <ol>
    <li></li>
    <li></li>
    <li></li>
    </ol>


* 什么是有序列表?
  * 有序列表的作用: 给一堆数据添加列表语义, 并且这一堆数据中所有的数据都有先后之分

### 2.1 有序列表格式:

```html
<ol>
    <li></li>
    <li></li>
</ol>
```

显示如下

<ol>
    <li></li>
    <li></li>
</ol>

其它用法和ul都差不多, 也就是应用场景/注意点都和ul差不多



## 3. 定义列表

```html
<dl>
    <dt>标题</dt>
    <dd>描述</dd>
    <dt>标题</dt>
    <dd>描述</dd>
</dl>
```

显示如下

* <dl>
    <dt>标题</dt>
    <dd>描述</dd>
    <dt>标题</dt>
    <dd>描述</dd>
    </dl>

* 定义列表的作用:
  1.1给一堆数据添加列表语义
  1.2先通过dt标签定义列表中的所有标题, 然后再通过dd标签给每个标题添加描述信息

* dt和dd都是英文的缩写
  * dt是英文definition title的缩写, 所以dt的含义就是用来定义列表中的标题
  * dd是英文definition description的缩写, 所以dd的含义就是用来定义标题对应的描述的

* 定义列表的应用场景
  1. 做网站尾部的相关信息
  2. 做图文混排

* 定义列表的注意点
  1. 和ul/ol一样, dl和dt/dd是一个整体, 所以他们一般情况下不会单独出现, 都是一起出现
  2. 和ul/ol一样, 由于dl和dt/dd是一个组合标签, 所以dl中建议只放dt和dd标签
  3. 一个dt可以没有对应的dd,也可以有多个对应的dd, 但是无论有或者没有dd都不推荐使用.
     * 推荐使用一个dt对应一个dd
  4. 和li标签一样, 当需要丰富界面时, 我们可以在dt和dd标签中继续添加其它标签





# 三、表格标签

``` html
<table>
    <tr>
        <td>需要显示的内容1</td>
        <td>需要显示的内容2</td>
    </tr>
        <td>需要显示的内容1</td>
        <td>需要显示的内容2</td>
    </tr>
</table>
```

显示如下

<table>
    <tr>
        <td>需要显示的内容1</td>
        <td>需要显示的内容2</td>
    </tr>
        <td>需要显示的内容1</td>
        <td>需要显示的内容2</td>
    </tr>
</table>



* 其实在过去表格标签用的非常非常的多, 绝大多数的网站都是使用表格标签来制作的, 也就是说表格标签是一个时代的代表



## 3.1 什么是表格标签?

* 表格标签作用: 用来给一堆数据添加表格语义
  * 其实表格是一种数据的展现形式, 当数据量非常大的时候, 表格这种展现形式被认为是最为清晰的一种展现形式
  * 其实表格标签中的table代表整个表格, 也就是一堆table标签就是一个表格
  * 其实表格标签中的tr标签代表整个表格中的一行数据, 也就是说一对tr标签就是表格中的一行
  * 其实表格标签中的td标签代表表格中一行中的一个单元格, 也就是说一对td标签就是一行中的一个单元格

## 3.2 注意点

1. 表格标签有一个边框属性, 这个属性决定了边框的宽度. 默认情况下这个属性的值是0, 所以看不到边框
2. 表格标签和列表标签一样, 它是一个组合标签, 所以table/tr/td要么一起出现, 要么一起不出现, 不会单个出现
   



## 3.3 表格标签的属性

```html
<table border="1" width="500px" height="300px" align="right" cellspacing="12px" cellpadding="1">
    <tr valign="bottom">
        <td width="150px" height="50px">1.1</td>
        <td valign="top">1.2</td>
    </tr>
    <tr align="center">
        <td align="right">2.1</td>
        <td>2.2</td>
    </tr>
</table>
```



<table border="1" width="500px" height="300px" align="right" cellspacing="12px" cellpadding="1">
    <tr valign="bottom">
        <td width="150px" height="50px">1.1</td>
        <td valign="top">1.2</td>
    </tr>
    <tr align="center">
        <td align="right">2.1</td>
        <td>2.2</td>
    </tr>
</table>








## 3.4 宽度和高度的属性

* 可以给table标签和td标签使用
  1. 表格的宽度和高度默认是按照内容的尺寸来调整的, 也可以通过给table标签设置width/height属性的方式来手动指定表格的宽度和高度
  2. 如果给td标签设置widht/height属性, 会修改当前单元格的宽度和高度, 不会影响整个表格的宽度和高度


1. 水平对齐和垂直对齐的属性
   * 其中水平对齐可以给table标签和tr标签和td标签使用
   * 垂直对齐只能给tr标签和td标签使用
     1. 给table标签设置align属性, 可以控制表格在水平方向的对齐方式
     2. 给tr标签设置align属性, 可以控制当前行中所有单元格内容的水平方向的对齐方式
     3. 给td标签设置align属性, 可以控制当前单元格中内容在说方向的对齐方式
        1. 注意点: 如果td中设置了align属性, tr中也设置了align属性, 那么单元格中的内容会按照td中设置的来对齐
     4. 给tr标签设置valign属性, 可以控制当前行中所有单元格中的内容, 在垂直方向的对齐方式
     5. 给td标签设置valign属性, 可以控制当前单元格中的内容在垂直方向的对齐方式

* 注意点:  如果td中设置了valign属性, tr中也设置了valign属性, 那么单元格中的内容会按照td中设置的来对齐



2. 外边距和内边距的属性
   * 只能给table标签使用
     * 外边距就是单元格和单元格之间的距离, 我们称之为外边距
       * 默认情况下单元格和单元格之间的外边距的距离是2px

3. 内边距就是单元格的边框和文字之间的间隙, 我们称之为内边距
   * 默认情况下**内边距是1**

* 注意:  以后在企业开发中所有控制样式的都是通过CSS



## 3.5 表格标签的其它标签

1. 表格标题
   * 在表格标签中提供了一个标签专门用来设置表格的标题, 这个标签叫做**caption**. 只要将标题写在caption标签中, 那么标题就会自动相对于表格的宽度居中
   * caption标签的注意点:
     1. caption一定要写在table标签中, 否则无效
     2. caption一定要紧跟在table标签后面
2. 标题单元格标签 **th**
   * 在表格标签中提供了一个标签专门用来存储每一列的标题, 这个标签叫做th标签, 只要将当前列的标题存储在这个标签中就会**自动居中并且加粗文字**

* 到此为止我们就发现, 其实表格中有两种单元格, 一种是td, 一种是th. td是专门用来存储数据的, th是专门用来存储当前列的标题的



## 3.6 表格的结构


1.由于表格中存储的数据比较复杂, 为了方便管理和阅读以及提升语义, 我们可以对表格中存储的数据进行分类
表格中存储的数据可以分为4类
1.1表格的标题
1.2.表格的表头信息
1.3.表格的主体信息
1.4.表格的页尾信息

2.表格的完整结构

```html
<table>
    <caption>表格的标题</caption>
    <thead>
        <tr>
            <th>每一列的标题</th>
            <th>每二列的标题</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>数据</td>
            <td>数据</td>
        </tr>
                <tr>
            <td>数据2</td>
            <td>数据2</td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <td>附加信息</td>
            <td>附加信息</td>
        </tr>
    </tfoot>
</table>
```



<table>
    <caption>表格的标题</caption>
    <thead>
        <tr>
            <th>每一列的标题</th>
            <th>每二列的标题</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>数据</td>
            <td>数据</td>
        </tr>
        <tr>
            <td>数据2</td>
            <td>数据2</td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <td>附加信息</td>
            <td>附加信息</td>
        </tr>
    </tfoot>
</table>

* caption作用: 
  * 指定表格的标题
* thead作用: 
  * 指定表格的表头信息
* tbody作用: 
  * 指定表格的主体信息
* tfoot作用: 
  * 指定表格的附加信息

* 注意点:
  1. 如果我们没有编写tbody, 系统会系统给我们添加tbody
  2. 如果指定了thead和tfoot, 那么在修改整个表格的高度时, thead和tfoot有自己默认的高度, 不会随着表格的高度变化而变化



## 3.7 细线表格的制作方式:

1. 给table标签设置bgcolor
2. 给tr标签设置bgcolor
3. 给table标签设置cellspacing = "1px"



## 3.8 表格单元格合并

### 1.水平方向上的单元格合并

* 可以给td标签添加一个colspan属性, 来指定把某一个单元格当做多个单元格来看待(水平方向)

  * ```html
    <td colspan="2"></td>
    ```

  * 含义: 把当前单元格当做两个单元格来看待

* 注意点:
  1.由于把某一个单元格当做了多个单元格来看到, 所以就会多出一些单元格, 所以需要删掉一些单元格才能正常显示
  2.**一定要记住单元格合并永远都是向后或者向下合并, 而不能向前或者向上合并**

* ```html
  <table>
      <caption>表格的标题</caption>
      <thead>
          <tr>
              <th>每一列的标题</th>
              <th>每二列的标题</th>
          </tr>
      </thead>
      <tbody>
          <tr>
              <td colspan="2">数据</td>
              <td>数据</td>
          </tr>
          <tr>
              <td>数据2</td>
              <td>数据2</td>
          </tr>
      </tbody>
      <tfoot>
          <tr>
              <td>附加信息</td>
              <td>附加信息</td>
          </tr>
      </tfoot>
  </table>
  ```

* 显示如下

* <table>
      <caption>表格的标题</caption>
      <thead>
          <tr>
              <th>每一列的标题</th>
              <th>每二列的标题</th>
          </tr>
      </thead>
      <tbody>
          <tr>
              <td colspan="2">数据</td>
              <td>数据</td>
          </tr>
          <tr>
              <td>数据2</td>
              <td>数据2</td>
          </tr>
      </tbody>
      <tfoot>
          <tr>
              <td>附加信息</td>
              <td>附加信息</td>
          </tr>
      </tfoot>
  </table>



### 2.垂直方向上的单元格合并

* 可以给td标签设置一个rowspan属性, 来指定把某一个单元格当做多个单元格来看待(垂直方向)

  * ```html
    <td rowspan="2"></td>
    ```

  * 含义: 把当前单元格当做两个单元格来看待

* 显示如下

* ```html
  <table>
      <caption>表格的标题</caption>
      <thead>
          <tr>
              <th>每一列的标题</th>
              <th>每二列的标题</th>
          </tr>
      </thead>
      <tbody>
          <tr>
              <td rowspan="2">数据</td>
              <td>数据</td>
          </tr>
          <tr>
              <td>数据2</td>
              <td>数据2</td>
          </tr>
      </tbody>
      <tfoot>
          <tr>
              <td>附加信息</td>
              <td>附加信息</td>
          </tr>
      </tfoot>
  </table>
  ```

* 

* <table>
      <caption>表格的标题</caption>
      <thead>
          <tr>
              <th>每一列的标题</th>
              <th>每二列的标题</th>
          </tr>
      </thead>
      <tbody>
          <tr>
              <td rowspan="2">数据</td>
              <td>数据</td>
          </tr>
          <tr>
              <td>数据2</td>
              <td>数据2</td>
          </tr>
      </tbody>
      <tfoot>
          <tr>
              <td>附加信息</td>
              <td>附加信息</td>
          </tr>
      </tfoot>
  </table>







# 四、表单标签

## 1.input

```html
<form action="">
    <表单元素>
</form>
```

* 显示如下
	* <form action=""><表单元素></form>

* 常见的表单元素
* input标签,
  *  input标签有一个type属性, 这个属性有很多类型的取值, 取值的不同就决定了input标签的功能和外观不同

```html
<!--明文输入框-->
账号:<input type="text"><br>
<!--暗文输入框-->
密码:<input type="password"><br>

<!--给输入框设置默认值-->
账号:<input type="text" value="lnj"><br>
密码:<input type="password" value="123"><br>
```

* 显示如下

  * 明文输入框
    账号:<input type="text" value="log.wiki"><br>

  * 暗文输入框
    密码:<input type="password" value="log.wiki"><br>

  * 给输入框设置默认值

    账号:<input type="text" value="log.wiki"><br>
    密码:<input type="password" value="123"><br>



### 1. 单选框 type=radio

* 注意点:

  1. 默认情况下单选框不会互斥, **要想单选框互斥那么必须给每一个单选框标签都设置一个name属性, 然后name属性还必须设置相同的值**

  2. **要想让单选框默认选中某一个框子, 那么可以给input标签添加一个checked属性**

  3. 在HTML中如果属性的取值和属性的名称一样, 可以只写一个. 但是在XHTML中必须写上取值, 所以在企业开发中我们推荐大家不要省略取值

     ```html
         性别:
         <input type="radio" name="xx" checked>男
         <input type="radio" name="xx">女
         <input type="radio" name="xx" >保密<br>
     ```

     * 显示如下
     * 
     * 性别:
       <input type="radio" name="xx" checked>男
       <input type="radio" name="xx">女
       <input type="radio" name="xx" >保密<br>



### 2. 多选框 type=checkbox

```html
爱好:
<input type="checkbox">篮球
<input type="checkbox">足球
<input type="checkbox" checked="checked">棒球
<input type="checkbox" checked="checked">足浴
```

显示如下

* 爱好:
  <input type="checkbox">篮球
  <input type="checkbox">足球
  <input type="checkbox" checked="checked">棒球
  <input type="checkbox" checked="checked">足浴

### 3.定义按钮

* 可以通过value属性来给按钮指定标题

  * 作用: 配合JS完成一些操作

    * ```html
      <input type="button" value="我是按钮">
      ```

    *  <input type="button" value="我是按钮">

* 图片按钮.

  * ```html
    <input type="image" src="images/register.jpg">
    ```

  * <input type="image" src="data:image/png;base64,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" width="50px">
  
    
  
### 4. 重置按钮 type=reset

  * 作用: 用于清空表单中已经填写好的数据，
  
    * 重置为input的Value 也就是默认值
    * 注意点:
    * 如果想想改重置按钮默认的按钮标题可以通过value属性来修改
  
  * 代码
  * ```html
    <form>
    <input type="text" value="">
    <input type="reset" value="还原默认值">
    </form>
    ```

  * 效果如下
    * <form>
      	<input type="text" value="">
      	<input type="reset" value="点击还原默认值">
      </form>

    

      

### 5. 提交按钮

```html
<input type="submit">
```

* 作用:

  * 将表单中已经填写好的数据, 提交到远程服务器        

* 注意点:

  * 要想把表单中填写好的数据提交到远程服务器, 必须具备两个条件

    1. 需要给form表单添加一个action的属性, 通过这个action属性指定需要提交到的服务器地址

    2. 需要给需要提交到服务器的表单元素添加一个name属性




### 6. 隐藏域

* 作用 : 配合提交按钮将一些数据默默的悄悄咪咪的提交到服务器
  Ajax

* ```html
  <input type="hidden" name="cc" value="kukuku">
  ```

  

### 7. 文字和输入框关联

1. 默认情况下文字和输入框是没有关联关系的, 也就是说点击文字输入框不会聚焦, 如果想点击文字时让对应的输入框聚焦, 那么就需要让文字和输入框进行绑定

2. 要想让输入框和文字绑定在一起, 那么我们可以使用Label标签

3. 绑定的格式:

   1. 将文字利用label标签包裹起来

   2. 给输入框添加一个id属性

   3. 在label标签中通过for属性和输入框中的id进行绑定即可

      ```html
      <label for="account">账号:</label><input type="text" id="account">xxxxxxxxxx   <label for="account">账号:</label><input type="text" id="account">文字和输入框是没有关联
      ```

      * 效果

        <label for="account">账号:</label><input type="text" id="account">



### 8. datalist标签

* 作用: 给输入框绑定待选项

* datalist格式:

  * ```html
    <datalist>
        <option>待选项内容</option>
    </datalist>
    ```

  * 效果如下
  * <datalist>
      	<option>待选项内容</option>
      </datalist>

* 如何给输入框绑定待选列表
  1. 搞一个输入框
  2. 搞一个datalist列表
  3. 给datalist列表标签添加一个id
  4. 给输入框添加一个list属性,将datalist的id对应的值赋值给list属性即可
  
  * ```html
    请输入你的车型: 
    <input type="text" list="cars">
    <datalist id="cars">
        <option>奔驰</option>
        <option>宝马</option>
        <option>奥迪</option>
        <option>路虎</option>
        <option>宾利</option>
    </datalist>
    ```
  
  * 效果如下
  
  * 请输入你的车型: 
    <input type="text" list="cars">
  
    <datalist id="cars">
        <option>奔驰</option>
        <option>宝马</option>
        <option>奥迪</option>
        <option>路虎</option>
        <option>宾利</option>
    </datalist>

### 9. 更多



* 可以自动校验输入的内容是否符合邮箱的格式

  * ```html
    邮箱:<input type="email">
    ```

  * 邮箱:<input type="email">

  

* 可以自动校验输入的内容是否是URL地址

  * ```html
    域名:<input type="url">
    ```

  * 域名:<input type="url">

 


* 输入框中只能输入数字

  * ```html
    电话:<input type="number">
    ```

  * 电话:<input type="number">

* 可以通过日历来选择时间

  * ```html
    时间:<input type="date">
    ```

  * ​    时间:<input type="date">

  

* 可以通过取色板来选择颜色

  * ```html
    颜色: <input type="color"><br>
    <input type="submit">
    ```

  * 颜色: <input type="color"><br>

    <input type="submit">



## 2.select 标签

* 作用: 用于定义下拉列表

* 格式:

  * ```html
    <select>
        <optgroup label="分组名称">
            <option>列表数据</option>
        </optgroup>
    </select>
    ```

  * 效果如下

  * <select>
        <optgroup label="分组名称">
            <option>列表数据</option>
        </optgroup>
    </select>



* 注意点:
  1. 下拉列表不能输入内容, 但是可以直接在列表中选择内容
  2. 可以通过给option标签添加一个selected属性来指定列表的默认值
  3. 可以通过给option标签包裹一层optgroup标签来给下拉列表中的数据分类

### 2.1selected="selected"选中

```html
<select>
    <option>北京</option>
    <option>上海</option>
    <option>广州</option>
    <option>广西</option>
    <option selected="selected">武汉</option>
</select>
```

* 效果↓

* <select>
      <option>北京</option>
      <option>上海</option>
      <option>广州</option>
      <option>广西</option>
      <option selected="selected">武汉</option>
  </select>

### 2.2 Select案例

```html
<select>
    <optgroup label="北京">
        <option>朝阳区</option>
        <option>昌平区</option>
        <option>通州区</option>
    </optgroup>
    <optgroup label="广州">
        <option>天河区</option>
        <option>越秀区</option>
        <option>黄浦区</option>
    </optgroup>
</select>
```

<select>
    <optgroup label="北京">
        <option>朝阳区</option>
        <option>昌平区</option>
        <option>通州区</option>
    </optgroup>
    <optgroup label="广州">
        <option>天河区</option>
        <option>越秀区</option>
        <option>黄浦区</option>
    </optgroup>
</select>

## 3.textarea标签

* 作用: 定义一个多行输入框

* 格式:

  * ```html
    <textarea>
    </textarea>
    ```

  * 效果如下

  * <textarea>
    </textarea>

* 注意点:
  1. 默认情况下输入框可以无限换行
  2. 默认情况下输入框有自己的宽度和高度
  3. 可以通过cols和rows来指定输入框的宽度和高度, 但是虽然指定了列数和行数, 但是还是可以无限往下输入
  4. 默认情况下输入框是可以手动拉伸的




<hr>
* 指定宽度和高度

* ```html
  <textarea cols="20" rows="5">
  </textarea>
  ```

* 效果如下


<textarea cols="20" rows="5">
</textarea>


# 五、其他标签

## 1.video标签

* 作用: 播放视频

* 格式:

  * ```html
    <video src="">
    </video>
    ```

* video标签的属性

  1. src: 用于告诉video标签需要播放的视频地址
  2. autoplay: 用于告诉video标签是否需要自动播放视频
  3. controls: 用于告诉video标签是否需要显示控制条
  4. poster: 用于告诉video标签视频没有播放之前显示的占位图片
  5. loop: 一般用于做广告视频, 用于告诉video标签视频播放完毕之后是否需要循环播放
  6. preload: 预加载视频, 但是需要注意preload和autoplay相冲, 如果设置了autoplay属性, 那么preload属性就会失效
  7. muted:静音
  8. width/height: 和img标签中的一模一样

  ```html
  <!--<video src="images/sb1.webm" autoplay="autoplay" controls="controls"></video>-->
  <!--<video src="images/sb1.webm"  controls="controls" poster="images/NJ.jpg"></video>-->
  
  <video src="images/sb1.webm"  autoplay="autoplay" loop="loop" muted="muted" width="800px"></video>
  
  ----------------------
  <video autoplay="autoplay" controls="controls">
      <source src="images/sb1.webm" type="video/webm"></source>
      <source src="images/sb1.mp4" type="video/mp4"></source>
      <source src="images/sb1.ogg" type="video/ogg"></source>
  </video>
  ```
  

<video autoplay="autoplay" controls="controls">
    <source src="images/sb1.webm" type="video/webm"></source>
    <source src="images/sb1.mp4" type="video/mp4"></source>
    <source src="images/sb1.ogg" type="video/ogg"></source>
</video>



## 2. audio标签

* 作用: 播放音频

* 两种格式:

  * ```html
    <audio src="">
    </audio>
    ```

  * ```html
    <audio>
        <source src="" type="">
    </audio>
    ```

* 注意点:
  * audio标签的使用和video标签的使用基本一样, video中能够使用的属性在audio标签中大部分都能够使用, 并且功能都一样
  * 只不过有3个属性不能用, height/width/poster

<audio autoplay="autoplay" controls="controls">
    <source src="images/yinyue.mp3" type="audio/mp3">
</audio>


## 3.详情和概要标签

* 利用summary标签来描述概要信息
* 利用details标签来描述详情信息
  * 默认情况下是折叠展示, 想看见详情必须点击

* 格式:

  * ```html
    <details>
        <summary>概要信息</summary>
        详情信息
    </details>
    ```

  * 效果如下

  * <details>
        <summary>概要信息</summary>
        详情信息
    </details>





## 4. marquee跑马灯

* marquee标签
  * 作用: 跑马灯

* 格式:

  * ```html
    <marquee>内容</marquee>
    ```

  * <marquee>内容</marquee>

* 属性:
  * direction: 设置滚动方向 left/right/up/down
  * scrollamount: 设置滚动速度, 值越大就越快
  * loop: 设置滚动次数, 默认是-1, 也就是无限滚动
  * behavior: 设置滚动类型 slide滚动到边界就停止, alternate滚动到边界就弹回

* 注意点:
  * marquee标签不是W3C推荐的标签, 在W3C官方文档中也无法查询这个标签, 但是各大浏览器对这个标签的支持非常好
    

* 滚动方向

  * 向右

    * ```html
      <marquee direction="right">随便写点内容</marquee>
      ```

    * <marquee direction="right">随便写点内容</marquee>

  * 向上

    * ```html
      <marquee direction="up">随便写点内容</marquee>
      ```

    * <marquee direction="up">随便写点内容</marquee>

  * 向下

    * ```html
      <marquee direction="down">随便写点内容</marquee>
      ```

    * <marquee direction="down">随便写点内容</marquee>

  * 向左

    * ```html
      <marquee direction="left">随便写点内容</marquee>
      ```

    * <marquee direction="left">随便写点内容</marquee>


<hr>


* 设置滚动速度

  * ```html
    <marquee scrollamount="2">随便写点内容</marquee>
    <marquee scrollamount="100">随便写点内容</marquee>
    ```

  * <marquee scrollamount="2">随便写点内容</marquee>
    <marquee scrollamount="100">随便写点内容</marquee>

<hr>

* 设置滚动次数

  * ```html
    <marquee loop="1">随便写点内容</marquee>
    ```

  * <marquee loop="1">随便写点内容</marquee>

<hr>

* 设置滚动类型

    * ```html
  <marquee behavior="slide">滚动到边界停止</marquee>
  <marquee behavior="alternate">在区间重复滚动</marquee>
  
  *  <marquee behavior="slide">滚动到边界停止</marquee>
     <marquee behavior="alternate">在区间重复滚动</marquee>
  
* 图片滚动

* ```html
    <marquee scrollamount="10" behavior="alternate" >
        <img src="" alt="图片" width="50px">
    </marquee>
    ```

* <marquee scrollamount="10" behavior="alternate">
        <img src="data:image/png;base64,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" alt="图片" width="50px">
    </marquee>



## 5.字符实体

1. 在HTML中对空格/回车/tab不敏感, 会把多个空格/回车/tab当做一个空格来处理

2. 什么是字符实体?

   * 在HTML中有的字符是被HTML保留的, 有的HTML字符在HTML中是有特殊含义的, 是不能在浏览器中直接显示出来的, 那么这些东西要想显示出来就必须通过字符实体

   * ```html
     &nbsp; 空格, 一个&nbsp;就是一个空格, 有多少个&nbsp;就有多少个空格
     &lt; 小于符号 <
     (less than)
     &gt; 大于符号 >
     (greater than)
     &copy; 版权符号
     ```



