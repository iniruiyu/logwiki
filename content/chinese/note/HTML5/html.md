---
title: "标题在这个地方写"
meta_title: ""
description: "posts 文章的介绍"
date: 2025-05-21T05:00:00Z
image: "/images/gallery/01.jpg"
categories: ["hugo", "markdown"]
author: "ruiyu"
tags: ["hugo", "markdown"]
draft: false
---



## 1.基础标签

### 1.img

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
  

### 2.br

* br标签, 如何在HTML中换行? 可以使用br标签
  1. br标签作用: 换行
  1. br标签格式: <br>
  3. br标签的注意点:
     3.1多个br标签可以连续使用, 使用了多少个br标签就会换多少行
     3.2由于HTML的作用就是用来给文本添加语义, 而br标签的语义是不另起一个段落换行, 而在企业开发中一般情况下需要换行都是因为需要另起一个段落, 所以在企业开发中很少使用br标签


### 3.src="路径问题"

* 路径问题

  * 其实想给src属性赋值有两种方式
    1. 通过相对路径赋值(掌握)
       * 相对路径就是每次都从.html文件所在的文件夹开始查找, 我们称之为相对路径

1. 相对路径的使用

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


​         

       * 含义：在.html文件所在的文件夹中找到这个文件夹的上一级文件夹, 然后再在上一级文件夹中找到名称叫做QRCode.jpg
         其中../代表找到当前文件夹的上一级文件夹


2. 通过绝对路径赋值(了解)
   * 绝对路径就是每次都从指定的盘符开始查找
     * 格式: src="C:\Users\Jonathan_Lee\Desktop\HTML基础\QRCode.jpg"
     * 含义: 在C盘下找到Users文件夹, 然后在Users文件夹中找到Jonathan_Lee文件夹, 然后在Jonathan_Lee文件夹中找到Desktop文件夹, 然后在Desktop文件夹中找到HTML基础文件夹, 然后在HTML基础文件夹中找到名称叫做QRCode.jpg的图片

* 注意:
  1. 路径中不要出现中文, 否则可能出现未知问题
  2. 如果是通过"相对路径"来指定图片, 不能跨盘符
     2.1 例如.html文件在C盘, 那么不能去查找D盘图片

④.
<a href="" target="_blank/_self" title=""></a>
<!--
什么是a标签?
a标签的作用: 就是用于控制页面与页面之间跳转的
a标签的格式: <a href="指定需要跳转的目标界面">需要展现给用户查看的内容</a>

a标签中有一个叫做target属性, 这个属性的作用就是专门用于控制如何跳转
_self: 用于在当前选项卡中跳转, 也就是不新建界面跳转. 默认就是_self
_blank: 用于在新的选项卡中跳转, 也就是新建界面跳转

a标签中还有一个属性, 叫做title. a标签中的title和img标签中的title一样, 都是用来控制鼠标悬停时显示的提示文本的

注意点:
1.a标签不仅可以让文字可以点击, 还可以让图片也能够被点击
2.一个a标签必须有一个href属性, 否则a标签不知道要跳转到什么地方
3.如果通过a标签的href属性指定一个URL地址, 那么必须在地址前面加上http://或https://
4.a标签的href属性除了可以指定一个网络地址以外, 还可以指定一个本地地址
-->

⑤.
<base target="_blank">
<!--
base标签就是专门用来统一的指定当前网页中所有的超链接(a标签)需要如何打开

注意点:
1.base标签必须写在head标签的开始标签和结束标签之间
2.如果既在base中指定了target又在a标签中指定了target,那么浏览器会按照a标签中指定的来执行
-->

⑥.假链接

<!--
1.什么是假链接?
就是点击之后不会跳转的链接我们称之为假链接

2.假链接存在的意义:
在企业开发前期, 其它界面都没有写出来, 那么我们就不知道应该跳转到什么地方, 所以就只能使用假链接来代替. 当项目后期其它界面都已经完成时再将假链接体会为真链接

3.假链接的格式:
1.#
2.javascript:

4.两者之间的区别:
#的假链接会自动回到网页的顶部, 而javascript:的假链接不会自动回到网页顶部
-->

二、列表标签
<!--
1.什么是列表标签?
列表标签的作用: 给一堆数据添加列表语义, 也就是告诉搜索引擎告诉浏览器这一堆数据是一个整体

2.HTML中列表标签的分类
2.1无序列表(最多)(unordered list)
2.2有序列表(最少)(ordered list)
2.3定义列表(其次)(definition list)
-->

Ⅰ.无序列表
<ul>
    <li>广州</li>
    <li>北京</li>
    <li>上海</li>
    <li>武汉</li>
</ul>
<!--
3.无序列表作用:
给一堆数据添加列表语义, 并且这一堆数据中所有的数据都没有先后之分

什么叫有先后之分?
例如: 排行榜
什么叫没有先后之分?
例如: 中国有哪些城市

4.无序列表格式:
<ul>
    <li>需要显示的条目内容</li>
</ul>
li其实是英文list item的缩写
list是列表的意思
item是条目的意思
所以结合起来就是 列表条目的意思

5.注意点:
1.一定要记住ul标签是用来给一堆数据添加列表语义的, 而不是用来给他们添加小圆点的
2. ul标签和li标签是一个整体, 是一个组合. 所以一般情况下ul标签和li标签都是一起出现, 不会单个出现. 也就是说不会单独使用一个ul标签或者单独使用一个li 标签, 都是结合在一起使用
3.由于ul标签和li标签是一个组合, 所以ul标签中不推荐包含其它标签, 也就是说以后你在ul标签中只会看到li标签

无序列表应用场景:
1.新闻列表
2.商品列表
3.导航条

在企业开发中, li标签中的内容可能会很复杂, 所以我们可以继续在li标签中添加其它的标签来丰富我的界面
总结:
1.一定更要记住ul标签中最好只放li标签
2.但是li标签中还可以继续放其它的标签
webstrom 快速书写
ul>li*(4)
-->

Ⅱ.有序列表
<ol>
    <li></li>
    <li></li>
    <li></li>
</ol>

<!--
什么是有序列表?
有序列表的作用: 给一堆数据添加列表语义, 并且这一堆数据中所有的数据都有先后之分

有序列表格式:
<ol>
    <li></li>
</ol>

其它用法和ul都差不多, 也就是应用场景/注意点都和ul差不多

-->

Ⅲ.定义列表
<dl>
    <dt></dt>
    <dd></dd>
    <dt></dt>
    <dd></dd>
</dl>

1.定义列表的作用:
1.1给一堆数据添加列表语义
1.2先通过dt标签定义列表中的所有标题, 然后再通过dd标签给每个标题添加描述信息

2.dt和dd都是英文的缩写
dt是英文definition title的缩写, 所以dt的含义就是用来定义列表中的标题
dd是英文definition description的缩写, 所以dd的含义就是用来定义标题对应的描述的

3.定义列表的应用场景
1.做网站尾部的相关信息
2.做图文混排

4.定义列表的注意点
4.1和ul/ol一样, dl和dt/dd是一个整体, 所以他们一般情况下不会单独出现, 都是一起出现
4.2和ul/ol一样, 由于dl和dt/dd是一个组合标签, 所以dl中建议只放dt和dd标签
4.3一个dt可以没有对应的dd,也可以有多个对应的dd, 但是无论有或者没有dd都不推荐使用.
推荐使用一个dt对应一个dd
4.4和li标签一样, 当需要丰富界面时, 我们可以在dt和dd标签中继续添加其它标签





三、表格标签
<table>
    <tr>
        <td>需要显示的内容</td>
    </tr>
</table>
<!--
其实在过去表格标签用的非常非常的多, 绝大多数的网站都是使用表格标签来制作的, 也就是说表格标签是一个时代的代表

1.什么是表格标签?
表格标签作用: 用来给一堆数据添加表格语义
其实表格是一种数据的展现形式, 当数据量非常大的时候, 表格这种展现形式被认为是最为清晰的一种展现形式

其实表格标签中的table代表整个表格, 也就是一堆table标签就是一个表格
其实表格标签中的tr标签代表整个表格中的一行数据, 也就是说一对tr标签就是表格中的一行
其实表格标签中的td标签代表表格中一行中的一个单元格, 也就是说一对td标签就是一行中的一个单元格

3.注意点
3.1表格标签有一个边框属性, 这个属性决定了边框的宽度. 默认情况下这个属性的值是0, 所以看不到边框
3.2表格标签和列表标签一样, 它是一个组合标签, 所以table/tr/td要么一起出现, 要么一起不出现, 不会单个出现
-->




表格标签的属性
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
<!--
1.宽度和高度的属性
可以给table标签和td标签使用
1.1表格的宽度和高度默认是按照内容的尺寸来调整的, 也可以通过给table标签设置width/height属性的方式来手动指定表格的宽度和高度
1.2如果给td标签设置widht/height属性, 会修改当前单元格的宽度和高度, 不会影响整个表格的宽度和高度

2.水平对齐和垂直对齐的属性
其中水平对齐可以给table标签和tr标签和td标签使用
垂直对齐只能给tr标签和td标签使用
2.1给table标签设置align属性, 可以控制表格在水平方向的对齐方式
2.2给tr标签设置align属性, 可以控制当前行中所有单元格内容的水平方向的对齐方式
2.3给td标签设置align属性, 可以控制当前单元格中内容在说方向的对齐方式
注意点: 如果td中设置了align属性, tr中也设置了align属性, 那么单元格中的内容会按照td中设置的来对齐

2.4给tr标签设置valign属性, 可以控制当前行中所有单元格中的内容, 在垂直方向的对齐方式
2.5给td标签设置valign属性, 可以控制当前单元格中的内容在垂直方向的对齐方式
注意点:  如果td中设置了valign属性, tr中也设置了valign属性, 那么单元格中的内容会按照td中设置的来对齐

3.外边距和内边距的属性
只能给table标签使用
3.1.外边距就是单元格和单元格之间的距离, 我们称之为外边距
默认情况下单元格和单元格之间的外边距的距离是2px

3.2 内边距就是单元格的边框和文字之间的间隙, 我们称之为内边距
默认情况下内边距是1


注意:  以后在企业开发中所有控制样式的都是通过CSS


表格标签的其它标签
1.表格标题
在表格标签中提供了一个标签专门用来设置表格的标题, 这个标签叫做caption. 只要将标题写在caption标签中, 那么标题就会自动相对于表格的宽度居中
2.caption标签的注意点:
2.1caption一定要写在table标签中, 否则无效
2.2caption一定要紧跟在table标签后面

3.标题单元格标签
3.1.在表格标签中提供了一个标签专门用来存储每一列的标题, 这个标签叫做th标签, 只要将当前列的标题存储在这个标签中就会自动居中+加粗文字

3.2.到此为止我们就发现, 其实表格中有两种单元格, 一种是td, 一种是th. td是专门用来存储数据的, th是专门用来存储当前列的标题的
-->
-->



表格的结构
<!--
1.由于表格中存储的数据比较复杂, 为了方便管理和阅读以及提升语义, 我们可以对表格中存储的数据进行分类
表格中存储的数据可以分为4类
1.1表格的标题
1.2.表格的表头信息
1.3.表格的主体信息
1.4.表格的页尾信息

2.表格的完整结构
<table>
    <caption>表格的标题</caption>
    <thead>
        <tr>
            <th>每一列的标题</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>数据</td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <td>数据</td>
        </tr>
    </tfoot>
</table>

caption作用: 指定表格的标题
thead作用: 指定表格的表头信息
tbody作用: 指定表格的主体信息
tfoot作用: 指定表格的附加信息

3.注意点:
3.1.如果我们没有编写tbody, 系统会系统给我们添加tbody
3.2.如果指定了thead和tfoot, 那么在修改整个表格的高度时, thead和tfoot有自己默认的高度, 不会随着表格的高度变化而变化
-->
细线表格的制作方式:
1.给table标签设置bgcolor
2.给tr标签设置bgcolor
3.给table标签设置cellspacing = "1px"


表格单元格合并
<!--
1.水平方向上的单元格合并
可以给td标签添加一个colspan属性, 来指定把某一个单元格当做多个单元格来看待(水平方向)
例如:
<td colspan="2"></td>
含义: 把当前单元格当做两个单元格来看待

注意点:
1.由于把某一个单元格当做了多个单元格来看到, 所以就会多出一些单元格, 所以需要删掉一些单元格才能正常显示
2.一定要记住单元格合并永远都是向后或者向下合并, 而不能向前或者向上合并

2.垂直方向上的单元格合并
可以给td标签设置一个rowspan属性, 来指定把某一个单元格当做多个单元格来看待(垂直方向)
例如:
<td rowspan="2"></td>
含义: 把当前单元格当做两个单元格来看待
-->






四、表单标签
<form action="">
    <表单元素>
</form>

常见的表单元素
input标签, input标签有一个type属性, 这个属性有很多类型的取值, 取值的不同就决定了input标签的功能和外观不同



    <!--明文输入框-->
    账号:<input type="text"><br>
    <!--暗文输入框-->
    密码:<input type="password"><br>
    
    <!--给输入框设置默认值-->
    账号:<input type="text" value="lnj"><br>
    密码:<input type="password" value="123"><br>


<!--
    单选框
    注意点:
    1.默认情况下单选框不会互斥, 要想单选框互斥那么必须给每一个单选框标签都设置一个name属性, 然后name属性还必须设置相同的值
    2.要想让单选框默认选中某一个框子, 那么可以给input标签添加一个checked属性
    3.在HTML中如果属性的取值和属性的名称一样, 可以只写一个. 但是在XHTML中必须写上取值, 所以在企业开发中我们推荐大家不要省略取值
    -->
    性别:
    <input type="radio" name="xx" checked>男
    <input type="radio" name="xx">女
    <input type="radio" name="xx" >保密<br>

    <!--多选框-->
    爱好:
    <input type="checkbox">篮球
    <input type="checkbox">足球
    <input type="checkbox" checked="checked">棒球
    <input type="checkbox" checked="checked">足浴

<!--
    定义普通按钮
    可以通过value属性来给按钮指定标题
    作用: 配合JS完成一些操作
    -->
    <input type="button" value="我是按钮">
    <!--
    图片按钮
    作用: 配合JS完成一些操作
    -->
    <input type="image" src="images/register.jpg">
    <!--
    重置按钮
    作用: 用于清空表单中已经填写好的数据
    注意点:
    如果想想改重置按钮默认的按钮标题可以通过value属性来修改
    -->
    <input type="reset" value="清空">
    <!--
    提交按钮
    作用: 将表单中已经填写好的数据, 提交到远程服务器
    注意点:
    要想把表单中填写好的数据提交到远程服务器, 必须具备两个条件
    1.需要给form表单添加一个action的属性, 通过这个action属性指定需要提交到的服务器地址
    2.需要给需要提交到服务器的表单元素添加一个name属性
    -->
    <input type="submit">
    
    <!--
    隐藏域
    作用 : 配合提交按钮将一些数据默默的悄悄咪咪的提交到服务器
    Ajax
    -->
    <input type="hidden" name="cc" value="kukuku">

1.默认情况下文字和输入框是没有关联关系的, 也就是说点击文字输入框不会聚焦, 如果想点击文字时让对应的输入框聚焦, 那么就需要让文字和输入框进行绑定

2.要想让输入框和文字绑定在一起, 那么我们可以使用Label标签

3.绑定的格式:
3.1将文字利用label标签包裹起来
3.2给输入框添加一个id属性
3.3在label标签中通过for属性和输入框中的id进行绑定即可
  <label for="account">账号:</label><input type="text" id="account">
-->


<!--
1.datalist标签
作用: 给输入框绑定待选项

2.datalist格式:
<datalist>
    <option>待选项内容</option>
</datalist>

3.如何给输入框绑定待选列表
1.搞一个输入框
2.搞一个datalist列表
3.给datalist列表标签添加一个id
4.给输入框添加一个list属性,将datalist的id对应的值赋值给list属性即可
-->
请输入你的车型: 
<input type="text" list="cars">
<datalist id="cars">
    <option>奔驰</option>
    <option>宝马</option>
    <option>奥迪</option>
    <option>路虎</option>
    <option>宾利</option>
</datalist>


更多
<!--
    可以自动校验输入的内容是否符合邮箱的格式
    -->
    邮箱:<input type="email"><br>
    <!--
    可以自动校验输入的内容是否是URL地址
    -->
    域名:<input type="url"><br>
    <!--
    输入框中只能输入数字
    -->
    电话:<input type="number"><br>
    <!--
    可以通过日历来选择时间
    -->
    时间:<input type="date"><br>

    <!--
    可以通过取色板来选择颜色
    -->
    颜色: <input type="color"><br>
    
    <input type="submit">




<!--
1.select标签
作用: 用于定义下拉列表

格式:
<select>
    <optgroup label="分组名称">
        <option>列表数据</option>
    </optgroup>
</select>

注意点:
1.下拉列表不能输入内容, 但是可以直接在列表中选择内容
2.可以通过给option标签添加一个selected属性来指定列表的默认值
3.可以通过给option标签包裹一层optgroup标签来给下拉列表中的数据分类

2.textarea标签
作用: 定义一个多行输入框

格式:
<textarea>
</textarea>

注意点:
1.默认情况下输入框可以无限换行
2.默认情况下输入框有自己的宽度和高度
3.可以通过cols和rows来指定输入框的宽度和高度, 但是虽然指定了列数和行数, 但是还是可以无限往下输入
4.默认情况下输入框是可以手动拉伸的
-->

<!--<select>-->
    <!--<option>北京</option>-->
    <!--<option>上海</option>-->
    <!--<option>广州</option>-->
    <!--<option>广西</option>-->
    <!--<option selected="selected">武汉</option>-->
<!--</select>-->

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

<hr>

<textarea cols="20" rows="5">
</textarea>



五、
<!--
1.什么是video标签?
作用: 播放视频

格式:
①<video src="">
</video>

video标签的属性
src: 用于告诉video标签需要播放的视频地址
autoplay: 用于告诉video标签是否需要自动播放视频
controls: 用于告诉video标签是否需要显示控制条
poster: 用于告诉video标签视频没有播放之前显示的占位图片
loop: 一般用于做广告视频, 用于告诉video标签视频播放完毕之后是否需要循环播放
preload: 预加载视频, 但是需要注意preload和autoplay相冲, 如果设置了autoplay属性, 那么preload属性就会失效
muted:静音
width/height: 和img标签中的一模一样
-->

<!--<video src="images/sb1.webm" autoplay="autoplay" controls="controls"></video>-->
<!--<video src="images/sb1.webm"  controls="controls" poster="images/NJ.jpg"></video>-->
<video src="images/sb1.webm"  autoplay="autoplay" loop="loop" muted="muted" width="800px"></video>
----------------------
<video autoplay="autoplay" controls="controls">
    <source src="images/sb1.webm" type="video/webm"></source>
    <source src="images/sb1.mp4" type="video/mp4"></source>
    <source src="images/sb1.ogg" type="video/ogg"></source>
</video>
②<!--
1.什么是audio标签?
作用: 播放音频

格式:
<audio src="">
</audio>

<audio>
    <source src="" type="">
</audio>

注意点:
audio标签的使用和video标签的使用基本一样, video中能够使用的属性在audio标签中大部分都能够使用, 并且功能都一样
只不过有3个属性不能用, height/width/poster
<audio autoplay="autoplay" controls="controls">
    <source src="images/yinyue.mp3" type="audio/mp3">
</audio>
-->
③.详情和概要标签
<!--
1.什么是详情和概要标签?
作用:利用summary标签来描述概要信息, 利用details标签来描述详情信息
默认情况下是折叠展示, 想看见详情必须点击

格式:
<details>
    <summary>概要信息</summary>
    详情信息
</details>
-->

④.
<!--
1.什么是marquee标签?
作用: 跑马灯

格式:
<marquee>内容</marquee>

属性:
direction: 设置滚动方向 left/right/up/down
scrollamount: 设置滚动速度, 值越大就越快
loop: 设置滚动次数, 默认是-1, 也就是无限滚动
behavior: 设置滚动类型 slide滚动到边界就停止, alternate滚动到边界就弹回

注意点:
marquee标签不是W3C推荐的标签, 在W3C官方文档中也无法查询这个标签, 但是各大浏览器对这个标签的支持非常好
-->

<!--滚动方向-->
<marquee>随便写点内容</marquee>
<marquee direction="right">随便写点内容</marquee>
<marquee direction="up">随便写点内容</marquee>
<marquee direction="down">随便写点内容</marquee>
<hr>
<!--设置滚动速度-->
<marquee scrollamount="1">随便写点内容</marquee>
<marquee scrollamount="100">随便写点内容</marquee>
<hr>
<!--设置滚动次数-->
<marquee loop="1">随便写点内容</marquee>
<hr>
<!--设置滚动类型-->
<marquee behavior="slide">随便写点内容</marquee>
<marquee behavior="alternate">随便写点内容</marquee>

<marquee>
    <img src="" alt="图片" width="50px">
</marquee>


⑤.字符实体
1.在HTML中对空格/回车/tab不敏感, 会把多个空格/回车/tab当做一个空格来处理


2.什么是字符实体?
在HTML中有的字符是被HTML保留的, 有的HTML字符在HTML中是有特殊含义的, 是不能在浏览器中直接显示出来的, 那么这些东西要想显示出来就必须通过字符实体

&nbsp; 空格, 一个&nbsp;就是一个空格, 有多少个&nbsp;就有多少个空格
&lt; 小于符号 <
(less than)
&gt; 大于符号 >
(greater than)
&copy; 版权符号

