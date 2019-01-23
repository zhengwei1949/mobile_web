# 移动web开发

---

​	重点在于使用百分比和px完成布局，难点在于js操作的几个特效

## 1.0 完成轮播图布局

​	轮播图的几个基本组件，由轮播图片列表，底部显示数量列表，左右点击按钮和相关文字说明组成

​	在移动端中，没有左右点击按钮，因为用户一般都由手指滑动来操作

综上，所需完成的功能，只有图片列表，底部显示的数量列表

### 基本布局

```html
<!-- 轮播图 -->
<div class="jd_banner">
	<ul class="jd_bannerImg clearfix">
		<li><a href="#"><img src="uploads/l1.jpg" alt=""></a></li>
		<li><a href="#"><img src="uploads/l2.jpg" alt=""></a></li>
		<li><a href="#"><img src="uploads/l3.jpg" alt=""></a></li>
		<li><a href="#"><img src="uploads/l4.jpg" alt=""></a></li>
		<li><a href="#"><img src="uploads/l5.jpg" alt=""></a></li>
        <li><a href="#"><img src="uploads/l6.jpg" alt=""></a></li>
        <li><a href="#"><img src="uploads/l7.jpg" alt=""></a></li>
        <li><a href="#"><img src="uploads/l8.jpg" alt=""></a></li>
	</ul>
    <ol class="jd_indicators">
        <li class="active"></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
	</ol>
</div>
```

​	`tips`：

​	正常来说，这里的图片数量和地址，还有底部计数的盒子，都是页面一打开发送请求，动态渲染出来的

### 相关样式

```css
/* banner site start */
.jd_banner {
    overflow: hidden;
    position: relative;
}

.jd_bannerImg {
    /* width: 800%; */
    position: relative;
}

.jd_bannerImg li {
    /* width: 12.5%; */
    float: left;
}

.jd_bannerImg li img {
    width: 100%;
}

.jd_indicators {
    position: absolute;
    left: 50%;
    bottom: 5px;
    transform: translateX(-50%);
}

.jd_indicators li {
    float: left;
    width: 6px;
    height: 6px;
    border-radius: 50%;
    border: 1px solid #fff;
    margin: 0 5px;
}

.jd_indicators li.active {
    background-color: #fff;
}
```



![banner](images\banner.jpg)



---



## 2.0 完成导航部分的布局



![nav-site](images\nav-site.jpg)



在排列导航的时候，一般都使用图标或者颜色块背景作为填充，并且每个盒子的大小都是一样的

​	所以在使用盒子的时候，基本都是4列(25%)，或者5列(20%)



### 基本布局

```html
<!-- 导航 -->
        <div class="jd_nav">
            <ul class="clearfix">
                <li>
                    <img src="uploads/nav1.png" alt="">
                    <p>京东物流</p>
                </li>
                <li>
                    <img src="uploads/nav2.png" alt="">
                    <p>京东超市</p>
                </li>
                <li>
                    <img src="uploads/nav3.png" alt="">
                    <p>京东到家</p>
                </li>
                <li>
                    <img src="uploads/nav4.png" alt="">
                    <p>充值缴费</p>
                </li>
                <li>
                    <img src="uploads/nav5.png" alt="">
                    <p>折扣优惠</p>
                </li>
                <li>
                    <img src="uploads/nav6.png" alt="">
                    <p>领券</p>
                </li>
                <li>
                    <img src="uploads/nav7.png" alt="">
                    <p>京东药店</p>
                </li>
                <li>
                    <img src="uploads/nav8.png" alt="">
                    <p>海屯全球</p>
                </li>
                <li>
                    <img src="uploads/nav9.png" alt="">
                    <p>生鲜</p>
                </li>
                <li>
                    <img src="uploads/nav10.png" alt="">
                    <p>全部</p>
                </li>
            </ul>
        </div>
```



### 相关样式

```css
/* jd_nav site start */
.jd_nav {
    background-color: #fff;
}

.jd_nav ul {
    padding: 12px 0;
}

.jd_nav li {
    float: left;
    width: 20%;
    text-align: center;
    padding: 10px 0;
}

.jd_nav li img {
    width: 44%;
    margin: 0 auto 10px;
}
```



`tips`　　　　

图标的大小应该由屏幕大小的改变而改变，后期会介绍rem作为变化的单位，目前可以使用百分比



---



## 3.0 完成产品信息布局



​	观察规律得出，这里的产品的结构都是差不多的

### 基本布局

```html
<div class="jd_product">
	<div class="jd_productBox">
    	<div class="jd_pTip">
        	<h3>京东超市</h3>
        </div>
        <div class="jd_pContent clearfix">
        	<a href="#"><img src="uploads/cp1.jpg" alt=""></a>
            <a href="#"><img src="uploads/cp2.jpg" alt=""></a>
            <a href="#"><img src="uploads/cp3.jpg" alt=""></a>
        </div>
	</div>
</div>
```



### 相关样式

```css
/* productBox site start */
.jd_productBox {
    margin-top: 10px;
    background-color: #fff;
    box-shadow: 2px 2px 2px rgba(0, 0, 0, .1);
}

.jd_pTip h3 {
    padding-left: 30px;
    font-size: 16px;
    line-height: 40px;
    position: relative;
    border-bottom: 1px solid #ccc;
}

.jd_pTip h3::before {
    content: "";
    position: absolute;
    top: 10px;
    left: 20px;
    width: 4px;
    height: 18px;
    background-color: #e92322;
}

.jd_pContent a {
    float: left;
    width: 50%;
}

.jd_pContent img {
    width: 100%;
}

.jd_pContent a:nth-of-type(2) {
    border-bottom: 1px solid #ccc;
}

.jd_pContent a:nth-last-of-type(-n+2) {
    border-left: 1px solid #ccc;
}

.pContent2 a:first-of-type {
    float: right;
    border-left: .5px solid #ccc;
}

```



​	__对于大部分都是一样的结构，后期会通过数据动态渲染__





### 秒杀专栏

![fast-skill](images\fast-skill.jpg)

#### 页面布局

```html
			<!-- 京东秒杀 -->
            <div class="jd_productBox jd_sk">
                <div class="jd_pTip clearfix">
                    <div class="jd_left">
                        <span class="jd_sk_icon"></span>
                        <span class="jd_sk_text">掌上秒杀</span>
                        <div class="jd_sk_time">
                            <span>0</span>
                            <span>0</span>
                            <span>:</span>
                            <span>0</span>
                            <span>0</span>
                            <span>:</span>
                            <span>0</span>
                            <span>0</span>
                        </div>
                    </div>
                    <div class="jd_right">更多秒杀...</div>
                </div>
                <div class="jd_pContent">
                    <ul class="clearfix">
                        <li>
                            <a href="#">
                                <img src="uploads/detail01.jpg" alt="">
                            </a>
                            <p><del>&yen;200.00</del></p>
                            <p>&yen;100.00</p>
                        </li>
                        <li>
                            <a href="#">
                                <img src="uploads/detail01.jpg" alt="">
                            </a>
                            <p><del>&yen;200.00</del></p>
                            <p>&yen;100.00</p>
                        </li>
                        <li>
                            <a href="#">
                                <img src="uploads/detail01.jpg" alt="">
                            </a>
                            <p><del>&yen;200.00</del></p>
                            <p>&yen;100.00</p>
                        </li>
                    </ul>
                </div>
            </div>
```



#### 相关样式

```css
/* fast shooping */
.jd_sk {
    padding-top: 10px;
}

.jd_sk .jd_pTip {
    padding-left: 20px;
}

.jd_sk_icon {
    width: 16px;
    height: 25px;
    float: left;
    background: url("../uploads/seckill-icon.png") no-repeat;
    background-size: 16px auto;
}

.jd_sk_text {
    float: left;
    color: #e92322;
    font-size: 14px;
    margin: 0 10px;
}

.jd_sk_time {
    float: left;
}

.jd_sk_time span {
    display: inline-block;
    width: 13px;
    height: 18px;
    background-color: #000;
    color: #fff;
    text-align: center;
    line-height: 18px;
    font-size: 14px;
}

.jd_sk_time span:nth-of-type(3n) {
    background-color: transparent;
    color: #333;
    width: 8px;
}

.jd_right {
    float: right;
    margin-right: 10px;
    font-size: 14px;
}

.jd_sk .jd_pContent ul li {
    width: 33.33%;
    float: left;
    text-align: center;
}

.jd_sk .jd_pContent ul li a {
    float: none;
    margin: 10px auto;
}

.jd_sk .jd_pContent p {
    font-size: 14px;
}
```



---



## 4.0 导航栏特效



```javascript
	// 1.0 搜索栏的背景透明
    window.onscroll = function() {
        effect()
    }
    effect()
    function effect() {
        var bannerHeight = document.querySelector(".jd_banner").offsetHeight;
        var searchBox = document.querySelector(".jd_search");
        var opacity = 0;
        // 获取页面滚动出去的距离，有兼容问题
        var offsetTop = document.body.scrollTop || document.documentElement.scrollTop;
        // 判断当前滚动出去的距离是否小于banner的高度
        if(offsetTop < bannerHeight) {
            opacity = offsetTop / bannerHeight;
        } else {
            opacity = 1;
        }
        // 判断完成之后接收opacity的值设置给盒子
        searchBox.style.backgroundColor = "rgba(233, 35, 34 , "+ opacity +")";
    }
```



```javascript
// 封装获取兼容后页面滚动出去距离的代码
function scroll() {
	return {
		top: window.pageYOffset || document.documentElement.scrollTop || document.body.scrollTop || 0,
        left: window.pageXOffset || document.documentElement.scrollLeft || document.body.scrollLeft || 0
    };
}
```



---



## 5.0 倒计时特效

 

```javascript
	// 2.0 倒计时秒杀
    var spans = document.querySelector(".jd_sk_time").children;
    var totalTime = 3700; // 以后的时间均来自于服务器
    var timer = setInterval(function() {
        calTime()
    }, 1000) 
    calTime() // 不需要等待执行
    function calTime() {
        totalTime--
        if(totalTime < 0) {
            // 如果到达时间后退出执行
            clearInterval(timer)
            return
        }
        // 获取时分秒
        var hour = Math.floor(totalTime / 3600);
        var mins = Math.floor(totalTime % 3600 / 60);
        var second = Math.floor(totalTime % 60);
        // 设置每一个盒子的内容
        spans[0].innerText = Math.floor(hour / 10);
        spans[1].innerText = Math.floor(hour % 10);
        spans[3].innerText = Math.floor(mins / 10);
        spans[4].innerText = Math.floor(mins % 10);
        spans[6].innerText = Math.floor(second / 10);
        spans[7].innerText = Math.floor(second % 10);
    }
```



---



## 6.0 完成自动轮播图



```javascript
// 3.0 处理轮播图的结构和样式
    bannerEffect()
    function bannerEffect() {
        var index = 1;
        // 3.1 修改结构，添加首尾图片
        var bannerBox = document.querySelector(".jd_banner");
        var ulBox = bannerBox.children[0];
        var firstLi = ulBox.children[0];
        var lastLi = ulBox.querySelector("li:last-of-type");
        // 把第1个li深层克隆一份，追加到ul中
        ulBox.appendChild(firstLi.cloneNode(true));
        // 把最后一个li深层克隆一份，置于第1个li之前
        ulBox.insertBefore(lastLi.cloneNode(true), firstLi);

        var bannerWidth = bannerBox.offsetWidth;
        var count = ulBox.children.length;
        // 当屏幕大小发生改变的时候，及时修正当前盒子大小和位置
        window.onresize = function() {
            resizeBanner()
        }
        // 3.2 设置默认样式
        resizeBanner()
        function resizeBanner() {
            // 获取单张图片的宽度
            bannerWidth = bannerBox.offsetWidth;
            // 设置ul盒子的总宽度
            ulBox.style.width = count * bannerWidth + "px";
            for(var i = 0; i < count; i++) {
                // 设置每一个li标签的宽度
                ulBox.children[i].style.width = bannerWidth + "px"
            }
            // 设置ul盒子的默认偏移
            ulBox.style.left = -(index * bannerWidth) + "px";
        }

        // 3.3 设置自动轮播
        setInterval(function() {
            index++
            ulBox.style.transition = "left .3s ease-in-out"
            ulBox.style.left = -(index * bannerWidth) + "px";
            if(index == count - 1) {
                setTimeout(function() {
                    index = 1
                    ulBox.style.transition = "none"
                    ulBox.style.left = -(index * bannerWidth) + "px";
                }, 300)
            }
        }, 1000)
    }
```









































































































