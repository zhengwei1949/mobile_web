>
>
> # 移动web开发

---

​	主要理解touch事件和使用，完成轮播图



## 1.0 touch事件

```javascript
// 执行一次
box.addEventListener("touchstart", function() {
    console.log("touchstart")
})
// 持续执行
box.addEventListener("touchmove", function() {
    console.log("touchmove")
})
// 执行一次
box.addEventListener("touchend", function() {
    console.log("touchend")
})
```



### 1.1 touch事件中的手指数组

​	不难想象，在PC端操作元素，只能通过一个鼠标，而在移动端操作，可以出现多个手指

​	而在使用手指的时候，又会有多个状态，所以就有了以下不同

#### 1.1.1 屏幕内的手指

>touches

​	一般来处理一些屏幕手势操作

```javascript
// 通过事件源参数e来获取
box.addEventListener("touchstart", function(e) {
    console.log(e.touches)
    // 得到一个数组
})
```



#### 1.1.2 盒子内手指

>targetTouches

​	一般多用来处理一些网页特效，针对于某个盒子的操作

```javascript
// 通过事件源参数e来获取
box.addEventListener("touchstart", function(e) {
    console.log(e.targetTouches)
    // 得到一个数组
})
```



####1.1.3 盒子内增减的手指

> changedTouches

​	记录从无到有，从有到无的手指，如果同时的是多个，那么就会打印多个，一般都是一个

```javascript
// 通过事件源参数e来获取
box.addEventListener("touchstart", function(e) {
    console.log(e.changedTouches)
    // 得到一个数组
})
```



__总结：__

​	以往在PC端由于只有一个鼠标，所以拿到鼠标的事件源参数，就能够拿到当前鼠标的坐标信息，

​	而现在在移动端中，先要获取到当前的手指对象，才能获取到当前的坐标信息

而拿到的手指数组，需要通过索引才能拿到当前手指对象

```javascript
var disX;
// 获取当前元素的坐标信息
div.addEventListener("touchstart",function(e){
   	// 按下去的位置距离屏幕的位置  -- 基本不用
	startX= e.targetTouches[0].screenX; // screenY
    
    // 按下去的位置距离客户区的位置  -- 多用于首屏操作
    startY= e.targetTouches[0].clientY; // clientY
    
    // 按下去的位置距离页面文档的位置  -- 多用于页面中下部的操作
    startY= e.targetTouches[0].pageY; // pageY
});
```

---



##2.0 滑动轮播图处理

​	在当前的案例中，需要的坐标信息只是水平的，而且只需要用到clientX的值，使用pageX不是特别适合

### 2.1 轮播图基本实现

​	步骤1： 在按下时，获取当前的坐标信息

​	步骤2：手指滑动时，获取当前的坐标信息，减去之前的坐标信息，获取差值

​	步骤3：手指停止滑动时，判断当前的值是否需要移动图片，再判断向左还是向右

```javascript
// 设置需要存储坐标的变量
var startX,moveX,distanceX;
// 1.0 为ul添加触摸开始 (执行1次)
imgBox.addEventListener("touchstart",function(e){
	// 清除定时器
	clearInterval(timerId);
	// 1.1 获取最初的坐标信息
	startX = e.targetTouches[0].clientX;
});

// 2.0 注册持续滑动事件
imgBox.addEventListener("touchmove",function(e){
	// 2.1 时时获取最新的坐标信息
    moveX = e.targetTouches[0].clientX;
    // 2.2 用最新的坐标信息 - 最初的坐标信息 = 差值
    distanceX = moveX - startX;
    // 2.3 去掉过渡效果，不然在拖拽的时候会有延迟效果
    imgBox.style.transition = "none";
    // 2.4 实现ul的偏移，！！！注意这里要累加之前已经偏移出去的距离
    imgBox.style.left= -(index * bannerWidth) + distanceX + "px";
});
```

​	

###2.2 松开手指的后续操作 

​	实现了基本的滑动操作，接来下就是手指离开后的后续操作了

​	！！！ 注意，只有在手指拖动的时候才需要distance差值，其他任何时候都不需要

```javascript
// 3.0 触摸结束，松开手指
imgBox.addEventListener("touchend",function(e){
	// 3.1 获取在move中计算出来的差值
    if(Math.abs(distanceX) > 100){
    	// 3.1.1 根据distance的值判断方向
        if(distanceX > 0){ //上一张
        	index--;
        } else { //下一张
            index++;
        }
        // 3.1.2 设置翻页，也就是ul的偏移
        imgBox.style.transition = "left 0.5s ease-in-out";
        imgBox.style.left =  -(index * bannerWidth) + "px";
        
    // 3.2 如果用户滑动区间距离不大，就回弹回去
    } else if (Math.abs(distanceX) > 0){
        imgBox.style.transition = "left 0.5s ease-in-out";
        imgBox.style.left= -(index * bannerWidth) + "px";
    }
	
    // 3.3 重启定时器
    startTime();
});
```

​	

###2.3 对于特殊情况的判断

​	关键一步，过渡结束之后的监听，

​	不比之前封装的animate，这里没有过渡结束的回调函数，因为是CSS，所以必须要通过这个事件去监听

```javascript
// webkitTransitionEnd: 监听元素的过渡效果执行完毕，会触发这个事件
// 4.0 每次过渡执行完毕之后，都会执行以下函数
imgBox.addEventListener("webkitTransitionEnd",function(){
	// 4.1 如果到了最后一张(count-1)，回到索引1
    if(index == count-1){
		index = 1;
        imgBox.style.transition = "none";
        imgBox.style.left= -(index * bannerWidth) + "px";
        
    // 4.2 如果到了第一张(0)，回到索引count-2
    } else if(index==0) {
        index=count-2;
        imgBox.style.transition = "none";
        imgBox.style.left= -(index * bannerWidth) + "px";
    }
});
```



###2.4 设置事件截流

```javascript
// 6.0 实现手动轮播
var startX, moveX, distanceX;
// ！！！！声明标记
var isEnd = true;
imgBox.addEventListener("touchstart",function(e){
    clearInterval(timerId);
    startX= e.targetTouches[0].clientX;
});

// ！！！！使用标记
imgBox.addEventListener("touchmove",function(e){
	// 只有当标记为true才能进来执行
    if(isEnd){
    	moveX= e.targetTouches[0].clientX;
        distanceX=moveX-startX;
        imgBox.style.transition="none";
        imgBox.style.left=(-index*bannerWidth + distanceX)+"px";
    }
});

// ！！！！改变标记
imgBox.addEventListener("touchend",function(e){
	// 意味着下一次的touchmove将不再执行
	isEnd=false;
    if(Math.abs(distanceX) > 100){
    	if(distanceX > 0){
        	index--;
        } else { 
        	index++;
        }
        imgBox.style.transition="left 0.5s ease-in-out";
        imgBox.style.left= -index*bannerWidth+"px";
    } else if(Math.abs(distanceX) > 0){ 
        imgBox.style.transition="left 0.5s ease-in-out";
        imgBox.style.left=-index*bannerWidth+"px";
    }
    // 将上一次move所产生的数据重置为0
    startX=0;
    moveX=0;
    distanceX=0;
});

// ！！！！每一次真正执行完成了，才会打开标记
imgBox.addEventListener("webkitTransitionEnd",function(){
	if(index == count - 1){
    	index = 1;
        imgBox.style.transition = "none";
        imgBox.style.left = -(index * bannerWidth) + "px";
    } else if(index == 0){
        index = count - 2;
        imgBox.style.transition = "none";
        imgBox.style.left = -(index * bannerWidth) + "px";
    }
    // 设置小点
    setIndicator(index);
    
    // ！！！！在这里打开标记
    setTimeout(function(){
		isEnd=true;
        
        clearInterval(timerId);
        startTime();
    },100);
});
```



### 2.5 点标记的设置

​	当图片发生滚动的时候，表示数量的小点，也应该发生变化

```javascript
/*实现点标记*/
var indicators = banner.querySelector("ul:last-of-type").children;
function setIndicator(index){
	/*先清除其它li元素的active样式*/
	for(var i=0;i<indicators.length;i++){
		indicators[i].classList.remove("active");
    }
    /*为当前li元素添加active样式*/
    indicators[index-1].classList.add("active");
}
```



​	何时重启定时器，如何重启定时器？

​	如果不将定时器内的代码进行封装，则不好再重启

```javascript
var timerId; // 在touchstart中需要清除定时器
// 5.0 实现自动轮播
function startTime(){
	timerId=setInterval(function(){
        index++;
        imgBox.style.transition="left 0.5s ease-in-out";
        imgBox.style.left=(-index*bannerWidth)+"px";
        // 5.1 判断是否到最后一张，如果是则回到索引1的位置
        setTimeout(function(){
        	if(index==count-1){
            	index=1;
                imgBox.style.transition="none";
                // 偏移到指定的位置
                imgBox.style.left=(-index*bannerWidth)+"px";
                // ！！！！ 5.2 设置点标记的排他
                for(var i=0;i<indicators.length;i++){
                	indicators[i].classList.remove("active");
                }
                // 默认第一个点标记添加高亮
                indicators[0].classList.add("active");
            }
		},500);
	},1000);
}
startTime();
```





---



## 3.0 zepto的使用

​	原生代码，在写起来的时候，有很多操作很复杂，很繁琐，这时候要是有jquery就好了

​	在移动端中，可以直接使用jquery，不过有人设计了一套跟它一样，并且比他体积还小的框架库

​	就叫做zepto.js



​	它的体积更小，方法和jquery一模一样，并且多了一些手势的事件，只是比jquery少了一些功能函数

​	所以zepto又被戏称为“阉割版的jquery”...



> 使用zepto完成轮播图

###3.1 修改结构

​	要记得先引入zepto.js

```javascript
var banner = $(".jd_banner"); // 获取banner盒子
var bannerWidth = banner.width(); // 获取banner的宽度
var imgBox = banner.find("ul:first-of-type"); // 获取ul盒子
// 获取点标记的所有盒子
var indicators = banner.find("ul:eq(1)").find("li");

// 获取首尾两张图片
var first = imgBox.find("li:first-of-type");
var last = imgBox.find("li:last-of-type");

imgBox.append(first.clone()); // 在最后追加复制的第一张
imgBox.prepend(last.clone()); // 在最前插入复制的最后一张
```



### 3.2 修改样式

​	设置单张图片的宽度和ul的总宽度，并且当屏幕大小发生改变要重置

​	还有默认的一张图片的偏移

```javascript
// 设置ul盒子的宽度
var lis = imgBox.find("li");
var count = lis.length;
imgBox.width(count * bannerWidth);
// 设置每一个li标签的宽度
lis.each(function (index, ele) {
	$(ele).width(bannerWidth);
});
// 设置默认偏移
imgBox.css("left", -bannerWidth);
```



### 3.3 设置自动轮播

```javascript
// 定义图片索引
var index = 1;
// 1.0 设置ul盒子真正的位移动画，方便后期调用
function animation2() {
	imgBox.animate({
    	"left": -index * bannerWidth
    }, 200, "ease-in-out",
    function () { //动画执行完毕之后的回调
    	// 如果是最后一张，就去真正的第一张
        if (index == count - 1) { 
        	index = 1;
            imgBox.css("left", -index * bannerWidth);
        // 如果是第一张，就去倒数第二张
        } else if (index == 0) {
            index = count - 2;
            imgBox.css("left", -index * bannerWidth);
        }
        // 设置点标记
        indicators.removeClass("active").eq(index - 1).addClass("active");
    });
}

// 2.0 自动轮播的函数
function autoPlay() {
	index++;
	// 设置ul真正的位移动画和回调函数
	animation2();
}

// 3.0 开启定时器
var timerId = setInterval(autoPlay, 2000);
```



### 3.4 添加滑动轮播

​	由于zepto已经封装好了左右滑动的事件，所以不需要再去判断方向了

​	只是这样的话，就不能实现手指按下去的时候还可以自由滑动图片了

```javascript
// 左滑动
imgBox.on("swipeLeft", function () {
	clearInterval(timerId);
    autoPlay();
    setTimeout(function () {
    	timerId = setInterval(autoPlay, 2000);
    }, 500)
});

// 右滑动
imgBox.on("swipeRight", function () {
	clearInterval(timerId);
    index--;
    animation2();
    
    setTimeout(function () {
    	timerId = setInterval(autoPlay, 2000);
    }, 500)
});
```

