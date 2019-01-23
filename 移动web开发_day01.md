# 移动web开发
### 像素密度

​	PPI (Pixels Per Inch) 也叫像素密度，所表示的是每英寸所拥有的像素数量。

#### 屏幕尺寸（英寸）

​	![ping](images\ping.jpg)

#### 长度单位

​	px, em, %

​	__相对长度__： em相对于一个文字的大小，px相对于一个像素点的大小

​	__绝对长度__：一种固定的标准的计量单位



__结论： 在移动端不同的产品中, 分辨率有不同的体现，比如像苹果公司，在一定的宽度和高度之内，集成了更多的像素，为了让屏幕渲染的更加细腻__

```html
如果PPI越大，代表1英寸内集成的像素点越多，代表当前屏幕的画面越清晰，代表当前实际像素越小
如果PPI越小，代表1英寸内集成的像素点越少，代表当前屏幕的画面越粗糙，代表当前实际像素越大
```



### 设备独立像素

​	设备独立像素（又称设备无关像素 Device Independent Pixels 、密度独立性 Density Independent或设备独立[像素](https://baike.baidu.com/item/%E5%83%8F%E7%B4%A0)，简称DIP或DP）是一种物理[测量单位](https://baike.baidu.com/item/%E6%B5%8B%E9%87%8F%E5%8D%95%E4%BD%8D/7854563)，基于计算机控制的坐标系统和抽象像素（虚拟像素），由底层系统的程序使用，转换为物理[像素](https://baike.baidu.com/item/%E5%83%8F%E7%B4%A0)的应用

![independentPX](images\independentPX.png)



​	一般安卓机，1~1.5   苹果手机 2或者3， plus一般都是3





### CSS像素 和 物理像素

| 名词    | 解释                               | 特点        |
| ----- | -------------------------------- | --------- |
| CSS像素 | 在使用css布局的时候，给盒子赋值设置的单位，就是CSS像素单位 | 可以被改变，不准确 |
| 物理像素  | 计算机领域中，描述一个呈现画面最实际最真实的基础单位       | 不可以被改变，准确 |



---



## 02 - 2倍图

​	在开发移动页面的时候，为了在各类屏幕中都能精细的展示页面，有以下策略

​	1，设计稿以大为准，例如640px宽

​	2，使用比当前元素大几倍的图片，防止在渲染的时候，由于压缩像素，导致图片被放大而失真

​	3，设置视口等于当前物理像素的设备宽高

### 2倍图的处理



---



## 03 - 移动端的调试办法

### 移动端调试

​	在课程中，介绍到了两款软件

itools =》 这个是用来将手机投屏在电脑上，方便展示效果和教学的，与开发无关

ghostlab =》 在课程中提到，这款软件收费，但是可以卸载重装，这句话不符合逻辑，所以不推荐使用



​	调试的渠道一（推荐）：

使用浏览器自带的移动端模拟器调试，能解决日常80%以上的bug

![moniqi](images\moniqi.jpg)



​	真机调试的方式（推荐）：



1， 安装虚拟服务器

2，将项目放置在虚拟服务器的文件夹中

3，将手机和电脑连入同一个网络，谁连谁都无所谓

4，手机通过浏览器，访问电脑的ip地址打开页面



---



## 04 - 移动端的视口

​	前提：在PC端中没有视口的概念，因为页面是1比1的

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=0">
<!--
	参数1： 将视口的宽度设置为设备的宽度，这样页面就不会被默认视口缩小
	参数2： 将理想视口和默认视口的初始比例值设置为1，和上一行结合起来解决一些兼容问题
	参数3： 禁止用户使用手指捏合缩放
-->
```

​	

```html
<meta name="viewport" content="width=device-width,initial-scale=1,minimum-scale=1,maximum-scale=1,user-scalable=0">


```

在sublime或者webstorm中，可以使用快捷键的方式快速生成

​	meta:vp  再按一下tab键



---



## 05 - 京东项目

​	开始做任何一个项目，都要预先准备好相关的环境和资料，有条不紊的开展相关工作

### 新建项目文件夹和文件

​	![item](images\item.jpg)



### 建立公共样式的文件

​	在移动端中需要多声明一个手指点击有背景颜色显示的属性

```css
html, body, ul, ol , div, span, p, li, form, table, tr, td, img, input, a {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    /*去除移动端特有的点击出现背景颜色*/
    -webkit-tap-highlight-color: transparent; 
}

html, body {
    font-size: 16px;
    color: #666;
    font-family: Arial, Helvetica, sans-serif, "Microsoft Yahei";
}

ul, ol {
    list-style: none;
}

a {
    text-decoration: none;
    color: #333;
}

input, button {
    outline: none;
    border: none;
    border: 1px solid #ccc;
}

textarea {
    resize: none;
}

/* 新添加的一些样式 */
.clearfix::before,
.clearfix::after {
    content: "";
    display: block;
    height: 0;
    line-height: 0;
    visibility: hidden;
}
.clearfix::after {
    clear: both;
}

.fl_l {
    float: left;
}

.fl_r {
    float: right;
}
```



### 页面基本布局

​	所有的内容都基本放在一个大盒子之内

```html
    <div class="jd_layout">
        <!-- 头部导航 -->
        <div class="jd_search">
            <a href="javascript:;" class="jd_logo"></a>
            <form action="" class="jd_searchBox">
                <input type="text" placeholder="请输入商品类型">
            </form>
            <a href="javascript:;" class="jd_login">登录</a>
        </div>
        <!-- 轮播图 -->
        <div class="jd_banner"></div>
        <!-- 产品信息 -->
        <div class="jd_nav"></div>
        <!-- 底部 -->
        <div class="jd_footer"></div>
    </div>
```



### 导航布局



```css
.jd_layout {
    max-width: 640px;
    min-width: 320px;
    height: 100%;
    background-color: #ccc;
    margin: 0 auto;
}

/* jd_search start */
.jd_search {
    width: 100%;
    max-width: 640px;
    min-width: 320px;
    height: 40px;
    position: fixed;
    background-color: #e92322;
}

.jd_logo {
    width: 60px;
    height: 30px;
    position: absolute;
    top: 6px;
    left: 10px;
    background-image: url("../images/jd-sprites.png");
    background-size: 200px auto;
    background-position: 0 -108px;
}

.jd_login {
    width: 40px;
    height: 40px;
    line-height: 40px;
    position: absolute;
    top: 0;
    right: 0;
    color: #fff;
}

.jd_searchBox {
    margin: 0 40px 0 70px;
    height: 40px;
    padding: 5px 10px 0;
    position: relative;
}

.jd_searchBox::before {
    content: "";
    width: 27px;
    height: 23px;
    position: absolute;
    background: url("../images/jd-sprites.png");
    background-size: 200px auto;
    background-position: -56px -108px;
    left: 15px;
    top:9px;
}

.jd_searchBox input {
    width: 100%;
    height: 30px;
    border-radius: 15px;
    padding-left: 34px;
    font-size: 16px;
    color: #333;
}
```

















