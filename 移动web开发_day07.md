# 移动web开发

---



## 1.0 完成信息模块



### 完成结构

```html
<!--信息块-->
<div class="wjs_info hidden-xs">
    <div class="container">
        <div class="row">
            <div class="col-sm-6 col-md-4">
                <a href="javascript:;">
                    <div class="media">
                        <span class="media-left wjs_icon wjs_icon_E900"></span>
                        <div class="media-body">
                            <h4 class="media-heading">支持交易保障</h4>
                            <p>银联支持全程保障支持安全</p>
                        </div>
                    </div>
                </a>
            </div>
            <div class="col-sm-6 col-md-4">
                <a href="javascript:;">
                    <div class="media">
                        <span class="media-left wjs_icon wjs_icon_E900"></span>
                        <div class="media-body">
                            <h4 class="media-heading">支持交易保障</h4>
                            <p>银联支持全程保障支持安全</p>
                        </div>
                    </div>
                </a>
            </div>
            <div class="col-sm-6 col-md-4">
                <a href="javascript:;">
                    <div class="media">
                        <span class="media-left wjs_icon wjs_icon_E900"></span>
                        <div class="media-body">
                            <h4 class="media-heading">支持交易保障</h4>
                            <p>银联支持全程保障支持安全</p>
                        </div>
                    </div>
                </a>
            </div>
            <div class="col-sm-6 col-md-4">
                <a href="javascript:;">
                    <div class="media">
                        <span class="media-left wjs_icon wjs_icon_E900"></span>
                        <div class="media-body">
                            <h4 class="media-heading">支持交易保障</h4>
                            <p>银联支持全程保障支持安全</p>
                        </div>
                    </div>
                </a>
            </div>
            <div class="col-sm-6 col-md-4">
                <a href="javascript:;">
                    <div class="media">
                        <span class="media-left wjs_icon wjs_icon_E900"></span>
                        <div class="media-body">
                            <h4 class="media-heading">支持交易保障</h4>
                            <p>银联支持全程保障支持安全</p>
                        </div>
                    </div>
                </a>
            </div>
            <div class="col-sm-6 col-md-4">
                <a href="javascript:;">
                    <div class="media">
                        <span class="media-left wjs_icon wjs_icon_E900"></span>
                        <div class="media-body">
                            <h4 class="media-heading">支持交易保障</h4>
                            <p>银联支持全程保障支持安全</p>
                        </div>
                    </div>
                </a>
            </div>
        </div>
    </div>
</div>
```



###修改样式

```less
/*信息块样式*/
.wjs_info{
  padding: 30px;
  .wjs_icon{
    font-size: 30px;
  }
  .row{
    > div{
      margin-top:20px;
      > a:hover{
        color: @baseColor;
      }
    }
  }
}
```



---



## 2.0 标签页的使用



### 完成预约块

#### 结构

```html
<!--预约块-->
<div class="wjs_reverse hidden-xs">
    <div class="container">
        <div class="row">
            <div class="col-sm-9">
                <span class="wjs_icon wjs_icon_E906"></span>
                现在的 272 人在排队，累计预约交易成功 7571 次
                <a href="javascript:;">什么叫预约投标</a>
                <a href="javascript:;" class="reverse_now">立即预约</a>
            </div>
            <div class="col-sm-3">
                <span class="wjs_icon wjs_icon_E905"></span>
                <a href="javascript:;">微金所企业宣传片</a>
            </div>
        </div>
    </div>
</div>
```

#### 样式

```less
/*预约块样式*/
.wjs_reverse{
  height: 60px;
  line-height: 60px;
  border-top:1px solid #ccc;
  border-bottom:1px solid #ccc;
  .wjs_icon{
    font-size: 18px;
  }
  .reverse_now{
    color: @baseColor;
    border-bottom: 1px dashed @baseColor;
  }
  a:hover{
    color: @baseColor;
  }
}
```



### 2.1 导航块



#### 完成页面结构

```html
<!--产品块-->
<div class="wjs_product">
    <div class="container">
        <div class="tabs_parent">
            <ul class="nav nav-tabs" role="tablist">
                <li role="presentation" class="active"><a href="#p1" aria-controls="p1" role="tab" data-toggle="tab">特别推荐</a></li>
                <li role="presentation"><a href="#p2" aria-controls="p2" role="tab" data-toggle="tab">微投资</a></li>
                <li role="presentation"><a href="#p3" aria-controls="p3" role="tab" data-toggle="tab">微小宝</a></li>
                <li role="presentation"><a href="#p4" aria-controls="p4" role="tab" data-toggle="tab">月月盈</a></li>
                <li role="presentation"><a href="#p5" aria-controls="p5" role="tab" data-toggle="tab">稳赢宝</a></li>
                <li role="presentation"><a href="#p6" aria-controls="p6" role="tab" data-toggle="tab">海航通宝</a></li>
                <li role="presentation"><a href="#p7" aria-controls="p7" role="tab" data-toggle="tab">微金宝</a></li>
            </ul>
        </div>
        <div class="tab-content">
            <div role="tabpanel" class="tab-pane active" id="p1"></div>
            <div role="tabpanel" class="tab-pane" id="p2">2</div>
            <div role="tabpanel" class="tab-pane" id="p3">3</div>
            <div role="tabpanel" class="tab-pane" id="p4">4</div>
            <div role="tabpanel" class="tab-pane" id="p5">5</div>
            <div role="tabpanel" class="tab-pane" id="p6">6</div>
            <div role="tabpanel" class="tab-pane" id="p7">7</div>
        </div>
    </div>
</div>
```



####完成页面样式

```less
/*产品块样式*/
.wjs_product{
  clear: both;
  background-color: #eee;
  padding:20px;

  .tabs_parent{
    width: 100%;
    overflow: hidden;
  }
  /*导航项样式的修改*/
  .nav-tabs{
    > li{
      margin-bottom: 0px;
      padding:0px 15px;
      //margin:0px 15px;
      > a{
        line-height: 50px;
        border-radius: 0px;
        border: none;
        background-color: transparent;
      }
      > a:hover{
        border-bottom: 3px solid @baseColor;
      }
      &.active{
        >a,a:hover,a:focus{
          border: none;
          border-radius: 0;
          background-color: #eee;
          border-bottom: 3px solid @baseColor;
        }
      }
    }
  }
}
```



### 2.2 产品块

####完成页面结构

```html

        <div class="tab-content">
            <div role="tabpanel" class="tab-pane active" id="p1">
                <div class="container">
                    <div class="row">
                        <div class="col-sm-6 col-md-4">
                            <div class="wjs_pBox active">
                                <div class="wjs_pLeft">
                                    <p>新手体验1002期</p>
                                    <div class="row">
                                        <div class="col-xs-6">
                                            <p>起投金额(元)</p>
                                            <p>0.01万</p>
                                        </div>
                                        <div class="col-xs-6">
                                            <p>起投金额(元)</p>
                                            <p>0.01万</p>
                                        </div>
                                        <div class="col-xs-6">
                                            <p>起投金额(元)</p>
                                            <p>0.01万</p>
                                        </div>
                                        <div class="col-xs-6">
                                            <p>起投金额(元)</p>
                                            <p>0.01万</p>
                                        </div>
                                    </div>
                                </div>
                                <div class="wjs_pRight">
                                    <b>8</b>
                                    <sub>%</sub>
                                    <p>年利率</p>
                                </div>
                            </div>
                        </div>
                        <div class="col-sm-6 col-md-4">
                            <div class="wjs_pBox">
                                <div class="wjs_pLeft">
                                    <p>新手体验1002期</p>
                                    <div class="row">
                                        <div class="col-xs-6">
                                            <p>起投金额(元)</p>
                                            <p>0.01万</p>
                                        </div>
                                        <div class="col-xs-6">
                                            <p>起投金额(元)</p>
                                            <p>0.01万</p>
                                        </div>
                                        <div class="col-xs-6">
                                            <p>起投金额(元)</p>
                                            <p>0.01万</p>
                                        </div>
                                        <div class="col-xs-6">
                                            <p>起投金额(元)</p>
                                            <p>0.01万</p>
                                        </div>
                                    </div>
                                </div>
                                <div class="wjs_pRight">
                                    <div class="wjs_tip">
                                        <span data-toggle="tooltip" data-placement="top" title="微金宝">宝</span>
                                        <span data-toggle="tooltip" data-placement="top" title="北京市">北</span>
                                    </div>
                                    <b>8</b>
                                    <sub>%</sub>
                                    <p>年利率</p>
                                </div>
                            </div>
                        </div>
                        <div class="col-sm-6 col-md-4">
                            <div class="wjs_pBox">
                                <div class="wjs_pLeft">
                                    <p>新手体验1002期</p>
                                    <div class="row">
                                        <div class="col-xs-6">
                                            <p>起投金额(元)</p>
                                            <p>0.01万</p>
                                        </div>
                                        <div class="col-xs-6">
                                            <p>起投金额(元)</p>
                                            <p>0.01万</p>
                                        </div>
                                        <div class="col-xs-6">
                                            <p>起投金额(元)</p>
                                            <p>0.01万</p>
                                        </div>
                                        <div class="col-xs-6">
                                            <p>起投金额(元)</p>
                                            <p>0.01万</p>
                                        </div>
                                    </div>
                                </div>
                                <div class="wjs_pRight">
                                    <b>8</b>
                                    <sub>%</sub>
                                    <p>年利率</p>
                                </div>
                            </div>
                        </div>
                        <div class="col-sm-6 col-md-4">
                            <div class="wjs_pBox">
                                <div class="wjs_pLeft">
                                    <p>新手体验1002期</p>
                                    <div class="row">
                                        <div class="col-xs-6">
                                            <p>起投金额(元)</p>
                                            <p>0.01万</p>
                                        </div>
                                        <div class="col-xs-6">
                                            <p>起投金额(元)</p>
                                            <p>0.01万</p>
                                        </div>
                                        <div class="col-xs-6">
                                            <p>起投金额(元)</p>
                                            <p>0.01万</p>
                                        </div>
                                        <div class="col-xs-6">
                                            <p>起投金额(元)</p>
                                            <p>0.01万</p>
                                        </div>
                                    </div>
                                </div>
                                <div class="wjs_pRight">
                                    <b>8</b>
                                    <sub>%</sub>
                                    <p>年利率</p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <div role="tabpanel" class="tab-pane" id="p2">2</div>
            <div role="tabpanel" class="tab-pane" id="p3">3</div>
            <div role="tabpanel" class="tab-pane" id="p4">4</div>
            <div role="tabpanel" class="tab-pane" id="p5">5</div>
            <div role="tabpanel" class="tab-pane" id="p6">6</div>
            <div role="tabpanel" class="tab-pane" id="p7">7</div>
        </div>
```



#### 完成页面样式

```less
  /*产品详细信息块样式*/
  .wjs_pBox{
    height: 150px;
    margin-top: 20px;
    background-color: #fff;
    .wjs_pLeft{
      margin-right: 100px;
      height: 150px;
      padding-top:10px;
      font-size: 12px;
      > p{
        width: 100%;
        text-align: center;
        font-size: 16px;
      }
      .row {
        margin-left:-10px;
        margin-right:-10px;
        > div:nth-of-type(even){
          text-align: right;
        }
      }
    }
    .wjs_pRight{
      width: 100px;
      height: 150px;
      position: absolute;
      right: 15px;
      top: 20px;
      border-left:1px dashed #ccc;
      text-align: center;
      padding-top:30px;
      > .wjs_tip{
        width: 100%;
        position: absolute;
        left: 50%;
        top: 20px;
        transform: translateX(-50%);
        > span{
          cursor: pointer;
        }
        > span:first-of-type{
          color: red;
          border: 1px solid red;
        }
        > span:last-of-type{
          color: blue;
          border: 1px solid blue;
        }
      }
      > b{
        font-size: 40px;
        color: @baseColor;
      }
      > sub{
        color: @baseColor;
        bottom: 0;
      }
      &::before,&::after{
        content: "";
        width: 10px;
        height: 10px;
        border-radius: 50%;
        background-color: #eee;
        position: absolute;
        left: -5px;
      }
      &::before{
        top: -5px;
        box-shadow: 0px -1px 1px #ddd inset;
      }
      &::after{
        bottom: -5px;
        box-shadow: 0px 1px 1px #ddd inset;
      }
    }

    /*设置当前active样式*/
    &.active{
      background-color: @baseColor;
      >.wjs_pRight{
        > b,sub,p{
          color: #fff;
        }
      }
      > .wjs_pLeft{
        color: #fff;
        position: relative;
        /*使用伪添加左上角的标志*/
        &::before{
          content: "\e915";
          /*一定要记得设置字体*/
          font-family: "wjs";
          position: absolute;
          left: 0;
          top:-5px;
          font-size: 25px;
        }
      }
    }
  }
```



### 2.3 使用插件完成提示

#### 结构

```html
<div class="wjs_tip">
	<!--data-toggle="tooltip":说明当前插件/组件是一工具提示-->
	<!--data-placement="top"：提示出现的位置-->
	<span data-toggle="tooltip" data-placement="top" title="微金宝">宝</span>
	<span data-toggle="tooltip" data-placement="top" title="北京市">北</span>
</div>
```

#### 样式

```less
> .wjs_tip{
	width: 100%;
    position: absolute;
    left: 50%;
    top: 20px;
    transform: translateX(-50%);
    > span{
       cursor: pointer;
    }
    > span:first-of-type{
       color: red;
       border: 1px solid red;
    }
    > span:last-of-type{
       color: blue;
       border: 1px solid blue;
    }
}
```



### 2.4 完成滑动效果

```javascript
	/* 1.0 计算产品块导航项的原始宽度*/
    var ul = $(".wjs_product .nav-tabs");
    var lis = ul.find("li");
    var totalWidth = 0;//总宽度
    lis.each(function(index,ele){
        totalWidth = totalWidth + $(ele).innerWidth();
    })
    ul.width(totalWidth);

    /* 2.0 使用插件实现导航条的滑动操作*/
    var myScroll = new IScroll('.tabs_parent',{
        /*设置水平滑动，不允许垂直滑动*/
        scrollX: true, 
        scrollY: false
    });
```





---



##3.0 新闻模块



### 3.1 完成新闻模块

```html
<!--新闻块-->
<div class="wjs_news">
    <div class="container">
        <div class="row">
            <div class="col-md-2 col-md-offset-2">
                <h3 class="wjs_nTitle">全部新闻</h3>
            </div>
            <div class="col-md-1">
                <div class="wjs_newsLine hidden-xs hidden-sm"></div>
                <ul class="nav nav-tabs" role="tablist">
                    <li role="presentation" class="active"><a href="#home" aria-controls="home" role="tab" data-toggle="tab"><span class="wjs_icon wjs_icon_new01"></span></a></li>
                    <li role="presentation"><a href="#profile" aria-controls="profile" role="tab" data-toggle="tab"><span class="wjs_icon wjs_icon_new02"></span></a></li>
                    <li role="presentation"><a href="#messages" aria-controls="messages" role="tab" data-toggle="tab"><span class="wjs_icon wjs_icon_new03"></span></a></li>
                    <li role="presentation"><a href="#settings" aria-controls="settings" role="tab" data-toggle="tab"><span class="wjs_icon wjs_icon_new04"></span></a></li>
                </ul>
            </div>
            <div class="col-md-7">
                <div class="tab-content">
                    <div role="tabpanel" class="tab-pane active" id="home">
                        <ul class="wjs_newslist">
                            <li>
                                <a href="">
                                    <span class="hidden-xs">2016-01-22</span>【微公告】关于海航通宝22期项目募集期延长通知
                                </a>
                            </li>
                            <li>
                                <a href="">
                                    <span class="hidden-xs">2016-01-22</span>【微动态】世纪佳缘与百合网的投资人首善财富董事长吴正新一行莅临微金所调研指导
                                </a>
                            </li>
                            <li>
                                <a href="">
                                    <span class="hidden-xs">2016-01-22</span>【微动态】封面人物第六期 ▏万雅泉—— 手写心情的双鱼座美女
                                </a>
                            </li>
                            <li>
                                <a href="">
                                    <span class="hidden-xs">2016-01-22</span>【微公告】2016年7月11日微金所平台系统升级维护公告
                                </a>
                            </li>
                            <li>
                                <a href="">
                                    <span class="hidden-xs">2016-01-22</span>【微动态】微金所与前海航交所携手，正式推出安全优质的理财产品—海航金宝！
                                </a>
                            </li>
                            <li>
                                <a href="">
                                    <span class="hidden-xs">2016-01-22</span>【微动态】微金所七月电脑节，激情狂欢理财好礼送不停！
                                </a>
                            </li>
                            <li>
                                <a href="">
                                    <span class="hidden-xs">2016-01-22</span>【微还款】一周还款公告2016年7月11日-7月17日
                                </a>
                            </li>
                        </ul>

                    </div>
                    <div role="tabpanel" class="tab-pane" id="profile">2</div>
                    <div role="tabpanel" class="tab-pane" id="messages">3</div>
                    <div role="tabpanel" class="tab-pane" id="settings">4</div>
                </div>
            </div>
        </div>
    </div>
</div>
```





样式调整

```less
/*新闻块样式*/
.wjs_news{
  padding:20px;
  .wjs_nTitle{
    line-height:50px;
    font-size: 25px;
    border-bottom: 1px solid #ccc;
    text-align: center;
    position: relative;
    &::before{
      content: "";
      width: 8px;
      height: 8px;
      border-radius: 4px;
      border: 1px solid #ccc;
      position: absolute;
      bottom: -4px;
      right: -8px;
    }
  }
  /*添加虚线边框*/
  .wjs_newsLine{
    width: 1px;
    height: 100%;
    position: absolute;
    border-left: 1px dashed @baseColor;
    left:45px;
    top:0;
  }
  .nav-tabs{
    border-bottom: none;
    position: relative;
    > li {
      margin-bottom:60px;
      > a{
        background-color: #ccc;
        width: 60px;
        height: 60px;
        border-radius: 50%;
        border: none;
      }
      > a:hover{
        border: none;
        background-color: @baseColor;
      }
      &.active{
        > a, a:hover, a:focus{
          border: none;
          background-color: @baseColor;
        }
      }
      .wjs_icon{
        font-size: 30px;
        color: #fff;
      }
    }
    > li:last-of-type{
      margin-bottom: 0px;
    }
    /*使用媒体查询设置w在768~992之间的li元素的样式*/
    @media screen and (min-width: 768px) and (max-width: 992px){
      > li {
        margin:20px 30px;
      }
    }
    /*使用媒体查询设置w<768时li元素的样式*/
    @media screen  and (max-width: 768px){
      > li {
        margin:20px 0px;
        width: 25%;
      }
    }
  }

  /*新闻列表样式*/
  .wjs_newslist{
    list-style: none;
    > li {
      line-height:60px;
    }
  }
}
```





















































